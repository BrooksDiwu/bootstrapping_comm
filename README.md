# Bootstrapping

This notebook is includes how to use bootstrapping for A/B testing. It uses a data set from Kaggle which can be found here https://www.kaggle.com/datasets/sergylog/ab-test-data. This data is the revenue for two different groups from an A/B Test.

### EDA

The first thing that we do in the notebook is some exploratory data analysis. Through this EDA we find out that the dataset is very sparse and also includes some outliers. We will address how we deal with this later in the notebook.

### Initial Bootstrap Attempt

In our initial bootstrap we don't touch the data at all and instead we split the control and variant data and then split the data into a train and test group. We end up being off by 0.02 for the variant group and 0.11 for the control group. Let's see what we can do about this.

### Keeping the correct sample proportions

Our first attempt at fixing the data will be keeping the same sample proportions. Because 1.5% of the data is nonzero, we fix our train and test groups to also include 1.5% nonzero data points. Our variant group result does not really change but the control group turns out to be a much better estimator.

### Upsampling

Our next attempt introduces upsampling to try to deal with the issues of the data being sparse. It once again fails to change the result of the variant group but makes the control group mean much more accurate as it's only off by 0.007 now.

### Removing outliers

Last we try to remove the outliers to see what happens. We remove the value of $200 and find that the control group estimation actually gets worse while the variant group once again keeps the same result.

# Conclusion

While bootstrapping is a very useful technique, this notebook clearly shows to us that bootstrapping does not work very well in certain situations. In situations like this, where your data is very sparse, bootstrapping turns out to give pretty weak results.
