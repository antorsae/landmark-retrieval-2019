# Retrieval Challenge 2019 solution
by Andres Torrubia 

The solution consists of two steps to replicate our solution (0.10439 private 0.08832 public) for https://www.kaggle.com/c/landmark-retrieval-2019:

## [Single model CNN extraction + NN search](https://github.com/antorsae/landmark-retrieval-2019/blob/master/submission-trained.ipynb)

This notebook extracts the last convolution layer of a given architecture applied GeM pooling and performs L2 normalization.

It uses augmentation (images are LR flipped) so both the index and queries features
are duplicated.

Once features are extracted, it performs regular nearest neighbour search using PCA, whitening and L2 normalization
and the resuls are ready for a submission.

It also saves the results of nearest neighbour search for ensembling.

## [Ensembling](https://github.com/antorsae/landmark-retrieval-2019/blob/master/ensemble.ipynb)

This notebook takes the results of nearest neighbours search for each query (and flipped LR queries)
and aggregates distances of different runs (different architectures) and builds a submission accordingly.

For flipped LR images, we pick the minimum distance.

## Some results

![image](https://user-images.githubusercontent.com/1516746/58861894-bc6a6980-86af-11e9-8261-21b4ebc26bb3.png)
![image](https://user-images.githubusercontent.com/1516746/58861581-f7b86880-86ae-11e9-8dd8-de50cf35af97.png)
![image](https://user-images.githubusercontent.com/1516746/58861667-34845f80-86af-11e9-9493-c012847fe0d0.png)
