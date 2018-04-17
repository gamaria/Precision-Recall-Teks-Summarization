# Precision-Recall-Teks-Summarization
Menghitung Precision-Recall Text Summarization
Example of Precision-Recall metric to evaluate classifier output quality.

Precision-Recall is a useful measure of success of prediction when the classes are very imbalanced. In information retrieval, precision is a measure of result relevancy, while recall is a measure of how many truly relevant results are returned.

The precision-recall curve shows the tradeoff between precision and recall for different threshold. A high area under the curve represents both high recall and high precision, where high precision relates to a low false positive rate, and high recall relates to a low false negative rate. High scores for both show that the classifier is returning accurate results (high precision), as well as returning a majority of all positive results (high recall).

A system with high recall but low precision returns many results, but most of its predicted labels are incorrect when compared to the training labels. A system with high precision but low recall is just the opposite, returning very few results, but most of its predicted labels are correct when compared to the training labels. An ideal system with high precision and high recall will return many results, with all results labeled correctly.

Precision (P) is defined as the number of true positives (T_p) over the number of true positives plus the number of false positives (F_p).

P = \frac{T_p}{T_p+F_p}

Recall (R) is defined as the number of true positives (T_p) over the number of true positives plus the number of false negatives (F_n).

R = \frac{T_p}{T_p + F_n}

These quantities are also related to the (F_1) score, which is defined as the harmonic mean of precision and recall.

F1 = 2\frac{P \times R}{P+R}

Note that the precision may not decrease with recall. The definition of precision (\frac{T_p}{T_p + F_p}) shows that lowering the threshold of a classifier may increase the denominator, by increasing the number of results returned. If the threshold was previously set too high, the new results may all be true positives, which will increase precision. If the previous threshold was about right or too low, further lowering the threshold will introduce false positives, decreasing precision.

Recall is defined as \frac{T_p}{T_p+F_n}, where T_p+F_n does not depend on the classifier threshold. This means that lowering the classifier threshold may increase recall, by increasing the number of true positive results. It is also possible that lowering the threshold may leave recall unchanged, while the precision fluctuates.

The relationship between recall and precision can be observed in the stairstep area of the plot - at the edges of these steps a small change in the threshold considerably reduces precision, with only a minor gain in recall.

Average precision (AP) summarizes such a plot as the weighted mean of precisions achieved at each threshold, with the increase in recall from the previous threshold used as the weight:

\text{AP} = \sum_n (R_n - R_{n-1}) P_n

where P_n and R_n are the precision and recall at the nth threshold. A pair (R_k, P_k) is referred to as an operating point.

AP and the trapezoidal area under the operating points (sklearn.metrics.auc) are common ways to summarize a precision-recall curve that lead to different results. Read more in the User Guide.

Precision-recall curves are typically used in binary classification to study the output of a classifier. In order to extend the precision-recall curve and average precision to multi-class or multi-label classification, it is necessary to binarize the output. One curve can be drawn per label, but one can also draw a precision-recall curve by considering each element of the label indicator matrix as a binary prediction (micro-averaging).
