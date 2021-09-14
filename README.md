# TEDAR
TEDAR is a pharmacovigilance signal detection method  based on variable-length temporal splitting.
The main goal is to detect, for each specific drug-adr pair, a set of intervals having different lengths that are representative of the pair under consideration.
A set of overlapping intervals are extracted for each drug-adr pair by applying a temporal data-mining approach. The notion of homogeneous interval is introduced. The covariance coefficient is engaged for detecting cutting points between the intervals in order to extract only homogeneous intervals.
Then, a graph theory-based algorithm is applied for retrieving a final set of non-overlapping intervals. Finally, TEDAR uses the PRR statistics for evaluating the significance of the retrieved intervals. However, any other statistical method can be used for such a purpose.

The proposed approach detects a greater number of true signals, w.r.t. state-of-art fixed length approaches, without significantly increasing the number of false positives.
TEDAR also detects adverse reactions more promptly, months before the other methodologies. Moreover, the approach is not dependent on a user-specified parameter, that is the length of the intervals.

![Image](doc/method_illustration.png)
