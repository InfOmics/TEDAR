# TEDAR
TEDAR is a pharmacovigilance signal detection method  based on variable-length temporal splitting.

## Overview

The main goal is to detect, for each specific drug-adr pair, a set of intervals having different lengths that are representative of the pair under consideration.
A set of overlapping intervals are extracted for each drug-adr pair by applying a temporal data-mining approach. The notion of homogeneous interval is introduced. The covariance coefficient is engaged for detecting cutting points between the intervals in order to extract only homogeneous intervals.
Then, a graph theory-based algorithm is applied for retrieving a final set of non-overlapping intervals. Finally, TEDAR uses the PRR statistics for evaluating the significance of the retrieved intervals. However, any other statistical method can be used for such a purpose.

![Image](doc/method_illustration.png)

The above image represents the generation of a DAG of intervals for extracting non-overlapping homogeneous intervals within the timespan of a specific drug-adr pair. Starting homogeneous intervals are displayed as grey rectangles. The initial structure of the DAG is the set of ordered time points (in this case months), represented as nodes (blue nodes) and linked by single edges (blue edges). Initial intervals are embedded in the DAG by adding extra edges from the starting time point to the DAG node consecutive to the one representing the end of the interval (blu edges). For this reason, an extra node is queued to the DAG (white node) in order to represent intervals in which the endpoint is the end of the timespan. Final intervals (orange rectangles) are extracted from one of the possible shortest paths (yellow path) from the start to the end of the DAG.

TEDAR detects a greater number of true signals, w.r.t. state-of-art fixed length approaches, without significantly increasing the number of false positives.
TEDAR also detects adverse reactions more promptly, months before the other methodologies. Moreover, the approach is not dependent on a user-specified parameter, that is the length of the intervals.

## Software architecture

The TEDAR software was developed using Ruby inside jupyter notebook.  Reports are collected, stored and manipulated using Redis as database management system.
For the application of signal detection thresholds and the validation phase of drug-adrs detectect was used R.


### Data sources

We use as case study the surveillance database, named RNF (Rete Nazionale Farmacovigilanza), released by the Italian authority AIFA (Agenzia Italiana del Farmaco). The RNF database contains reports of ADRs issued by all the Italian regions.

ADRs are encoded according to the MedDRA (Medical Dictionary for Regulatory Activities) terminology, which consists of large set of terms structured into five hierarchical levels. System Organ Classes (SOC) are the level terminology used in this system to encode ADRs. SOC is the highest level of ADR terminology and terms here are distinguished by anatomical or physiological system, etiology or purpose.

Drug is defined as pharmaceutical product (combinations of active ingredients) according to the requirements of the ICH M5 standard adopted in RNF. We make no distinction between pharmaceutical products with the same combinations of active ingredients.

Data extraction from RNF was carried out through the Vigisegn data warehouse. Thanks to the ease of access to the registers and the ability to download the entire database, it was possible to retrieve the information necessary for the TEDAR analysis: <b> <report id, entry date, drugs (pharmaceutical products),  ADRs (SOC)></b>.


We used the ADReCS and PROTECT datasets contained verified drug-adr relations for assessing the performances of TEDAR.

## Contents

The srs folder contains all code used:

* **TEDAR.ipynb**: 
* **Compute_disproportionality.ipynb**: 
* **Validate.R**: 
  
  

## Authors and acknowledgment

Antonino Aparo(antonino.aparo@univr.it), Pietro Sala (pietro.sala@univr.it) and Vincenzo Bonnici (vincenzo.bonnici@univr.it) created the workflow. 

## License
[MIT](https://choosealicense.com/licenses/mit/)
