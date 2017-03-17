# **Clustering Methods**
     Clustering Analysis is to partition a set of N objects into C clusters such that objects within cluster should be similar to each other and objects in different clusters should be dissimilar to each other.
- # Hard Clustering
- # Soft Clustering
  * **Fuzzy C-means Clustering**
    1. Unsupervised method
    2. Algorithm
      ![](assets\2017-03-12-16-34-11.png)
      This algorithm works by assigning membership to each data point corresponding to each cluster on the basis of distance between the cluster center and the data point.
    3. Applications
    4. Advantages
       -> More natural than hard clustering, each data point can belong to more than one cluster with different membership grades between 0 and 1.
       -> Converges
    5. Disadvantages
       -> Long computational time
       -> Sensitivity to the initial guess(speed,local minima)
       -> Sensitivity to noise
          One expects low (or even no) membership degree for outliers(noisy points)
    6. Optimal number of clusters
       Performance index
       ![](assets\2017-03-12-17-19-45.png)
       ![](assets\2017-03-12-17-23-16.png)
    7. Possibilistic Fuzzy C-means clutering(PFCM)   **?**
    8. Fuzzy-Possibilistic C-means (FPCM)   **?**
      <a href="C:\Book\Knowledge base\Methods_Data mining\y_fcmc_presentation_v0.8" target="_blank">link</a>
      