# eeg_eyestate

This work is based on the data set from Rösler and Suendermann (2013). They made a 117 second electrogram (EEG) recording of a subject opening and closing their eyes at will using a widely available EEG headset (Emotiv EPOC headset, see images below). Eye state (open or closed) was confirmed by a simultaneous video recording. The resulting data set contains 14977 recorded instances.  Each instance consists of values from each of the 14 EEG sensors (corresponding to the illustration below) and eye state, open or closed, indicated by a 0 or 1. 

The authors used numerous machine learning algorithms with varying success on detecting eye state, with many well-known ML algorithms such as neural networks and random forests producing an error rate of 10% or greater. The best performing algorithm, K Star, accurately identified eye state 97% of the time, but required significant processing time even on high end hardware – nearly 40 minutes. The authors indicated that they did very little cleaning on the data set with mention of having removed three instances for “obvious transmission errors.”  The authors also did not indicate if the ML algorithms had optimized for best performance.

In my work with the dataset, after performing EDA tasks such as visualizing the attributes, I identified and removed an additional 4 instances with outliers (values above 4 standard deviations) and then re-centered and standardized the data set.  I then split the set into test and training sets (80/20 split) and trained a series of common machine learning algorithms – logistic regression, CART decision tree, random forest, neural network, support vector machine and K nearest neighbor.  The performance of each algorithm was optimized using the Caret package.  Out of the algorithms tested, K nearest neighbors performed the best, correctly identifying eye state 97% of the time with a run time of only a few seconds.

While I was able to achieve equivalent performance as the authors using a better-known, more easily understandable algorithm, this also comes with some caveats. Ideally, identification of eye state would occur in a “just-in-time” application operating with continuous data. In this use case, centering and standardizing the set would not be possible and other ways of filtering outliers would need to be explored. Future work should center on reducing the number of inputs while maintaining prediction accuracy.

[![EmotivEEG](https://github.com/dwagner239/eeg_eyestate/blob/master/emotivEEG.jpg)]

Rösler, O., & Suendermann, D. (2013). A first step towards eye state prediction using EEG. Proc. of the AIHLS, 1, 1-4. (http://www.oeft.com/su/pdf/aihls2013.pdf)
EEG Eye State dataset available at https://archive.ics.uci.edu/dataset/264/eeg+eye+state
