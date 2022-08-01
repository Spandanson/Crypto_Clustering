
# Cryptocurrency Clustering - Unsupervised Machine Learning
## Objective:
Pretend a prominent investment bank is interested in offering a new cryptocurrency investment portfolio for its customers. The company, however, is lost in the vast universe of cryptocurrencies. So, they’ve asked me to create a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.

The data I will be working with is not ideal, so it will need to be processed to fit the machine learning models. Since there is no known output for what I am looking for, I have decided to use unsupervised learning. To group the cryptocurrencies, I decided on a clustering algorithm. I will use data visualizations to share hmyer findings with the board.
## Technologies Used:
* scikit-learn: https://scikit-learn.org/stable/getting_started.html
* hvplot: https://hvplot.holoviz.org/
## Background:
Using data gathered from CryptoCompare, the "world's leading digital asset data company", I processed the cryptocurrencies by only selecting coins that are currently traded, mined, and have a working algorithm. Once selected, I one-hot encoded the categorical data, then scaled the entire feature set.

Once the features were gathered, I performed Principal Component Analysis to reduce the total feature set down to three. I then performed a K-Means analysis to view possible clusters and groupings of the coins. After I selected the optimal cluster, I viewed the resulting cluster set.
## Data:
I used data from CryptoCompare, a populare API for historical and present cryptocurrency data.

* CryptoCompare: https://min-api.cryptocompare.com/
## Data Cleaning:
Once all coins had been downloaded, I only selected coins that are currently traded, mined, and have a working algorithm. I then dropped all coins with any null features. After this feature pre-processing, I one-hot encoded the categorical data, then scaled the entire feature set.

Principal Component Analysis

PCA is a statistical technique to speed up machine learning algorithms when the number of input features (or dimensions) is too high. PCA reduces the number of dimensions by transforming a large set of variables into a smaller one that contains most of the information in the original large set. PCA is a good feature reduction strategy when many columns exist and an analyst is worried about overfitting.

I chose to use 3 principal components for visualization purposes.

![](https://github.com/Spandanson/Crypto_Clustering/blob/master/Resources/pca.png)

Combined, only having three principal components accounted for less than 10% of the explained variance. This could be due to the fact that the feature set, including the encoded dummies, did not have much relation with each other.

![](https://github.com/Spandanson/Crypto_Clustering/blob/master/Resources/pca_exp.png)

However, three components can easily be viewed in 3D scatter plots, which made the communication post-clustering quite effective.
### K-Means Clustering
K-means is an unsupervised learning algorithm used to identify and solve clustering issues.

K represents how many clusters there will be. These clusters are then determined by the means of all the points that will belong to the cluster.

The K-means algorithm groups the data into K clusters, where belonging to a cluster is based on some similarity or distance measure to a centroid - the arithmetic mean position of all the points on a cluster.

An easy method for determining the best number for K is the elbow curve. Elbow curves get their names from their shape: they turn on a specific value, which looks a bit like an elbow! To create an elbow curve, we'll plot the clusters on the x-axis and the values of the corresponding inertia on the y-axis.

![](https://github.com/Spandanson/Crypto_Clustering/blob/master/Resources/Elbow%20curve.png)

When the three principal components are put through a K-Means analysis, the elbow plot indicates an obvious bend at k=4. With these features, the algorithm found an optimal way to group all of the cryptocurrencies into 4 classes.

### Visualizing Classes
I visualized the distinct groups that corresponded to the three principal components using 2D and 3D scatter plots. I also created a table with all the currently tradable cryptocurrencies and their predicted cluster.
![](https://github.com/Spandanson/Crypto_Clustering/blob/master/Resources/scatter3d.png)

I scaled the Total Coin Supply and Total Coins Mined columns to standardize the axes for the 2D scatter plot.

![](https://github.com/Spandanson/Crypto_Clustering/blob/master/Resources/scatter2d.png)
Finally, below are snapshots of the predicted classes.

![](https://github.com/Spandanson/Crypto_Clustering/blob/master/Resources/Group%200.png)

![](https://github.com/Spandanson/Crypto_Clustering/blob/master/Resources/Group%201.png)

![](https://github.com/Spandanson/Crypto_Clustering/blob/master/Resources/Group%202.png)

![](https://github.com/Spandanson/Crypto_Clustering/blob/master/Resources/Group%203.png)

## Summary and Conclusions:

Our study found that four clusters was optimal when the first three principal components for our data set were analyzed with K-Means.

Two of these clusters are about equal size, each containing a couple hundred coins. One of the clusters only has around a half-dozen coins. The last cluster has exactly one coin in its grouping.

Further investigation should be done to see if BitTorrent really is so unique in the crypto world. Further, coins in group 0 are all relatively popular and include Bitcoin, Ethereum, Litecoin, and Monero.

The results of this study should also understand the limitation caused by using three principal components. When the variance explained is examined, these three components only account for 7% of the total variance - not enough to constitue a robust replacement for all of the features dropped.





