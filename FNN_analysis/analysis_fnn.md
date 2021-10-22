[#](#) FNN: Determining the proper dimension
For noise-free data, the number of false neighbors will drop to zero when the dimensioin of the regression vector is large enough to allow accurate prediction of future ouputs

If the percentage of false neighbors is lagre, then the regressor vector must be extend to include more delayed input and/or output terms
## The threshold selection and data requirements

The one adjust parameter in the above algorithms is the threshold $R$ used in the ratio test. The proper choice of the threshold  is important. If $R$ is too small, then the percentage of false nearest neighbors may not drop tp zero in the proper dimension. On the other hand, if $R$ is too larger it is possible that the FNN algorithm will predict that future outputs are predictable with a regressor dimension that is too small. In order to properly select the threshold $R$ and understand the result of the FNN algorithm, analysisis of what passing or failing this threshold test refers to in a geometric sence will be given.

 Choosing a single threshold which will work well for all data set is an impossible task. Fortunately, it has been observed that false neighbors tend th have future outputs which are very different when the embedding dimension is too small. Therefore, the threshold can be safely made fairly large and the algorithm will give the result that the embedding dimension is too small for accurate prediction. The authors have observed that a good choice of the threshold is in the range of 10-15. When the time-series is relatively short, the choice of threshold is more critical and it might be necessary to compare the results from a number of different threholds to come to a resonanle conclusiono on the regressor size.
 
## Noise corruption
 
The FNN algorithm is not robust to the presence of noise in the time-series.

In order to solve this problem, a new threshold test can be used for time-series wherr significant noise corruption is expected. A logical form if this threshlod test based on the previous analysis is
$$\frac{|y(k)-y(j)|}{||\Psi_{l.m}(k)-\Psi_{l.m}(j)||_2}\leq R + \frac{2R\sqrt{l\epsilon^{y^2}+m\epsilon^{u^2}}+2\varepsilon^y}{||\Psi_{l.m}(k)-\Psi_{l.m}(j)||_2}$$
Notice that thsi threshold test has two distiinct limits. When the data are "dense", the second term on the right hand side will dominate. In this limit, the new threhold test simply determines whether the two neighbors outputs are within some specified noise-related distance $(2R\sqrt{l\epsilon^{y^2}+m\epsilon^{u^2}}+2\epsilon^y)$ of one another.

## Inferential measurement selection

If the percentage of false nearest neighbors is large for all combinations of measurements in the given regression dimension $l$, the number of secondary measurements in the regressor vector should be increased.

The basic trend we expect, and see, is that as the signal to noise ratio is lowered, the effective embedding dimension rises.

After separating the signal from the cintamination, one can easily go back to the false-nearest-neighbor method to determine another(probably smaller) embedding dimension to use in analyzing the signal.

We each use time-delay coordinates and attribute the disappearance of false neighbors as an indication of a minimum embedding dimension for the data.

For large $T$, the proportion of false neighbors and also the $W$ statistic increase, because the attractor looks more like noise, as the elements of the state-space vector become more decorrelated due to the positive Lyapunov exponent. For sufficiently small time lats, the attractor eventually collapses onto a one-dimension will be spuriously low. The division by $T$ appears to be a way of ameliorating the latter problem, if one then ignores new minima in $W$ created at large $T$ by the division.

In constrast to the case for embedding dimension, the theorems do not define a "correct" time dalay to use, rather one must choose a condition that simply gives reasonable results given a finite amount of data at a certain sampling rate, and the LPS criterion is another one to do so. Our method, as ti is attuned spcofically to the gross errors created by an imporper embedding, apears in parctice to be less sensitive to time delay than LPS'a method. This fact may be either a virtue or a vice, depending on one's outlook.
