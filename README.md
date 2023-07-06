
![performance](https://github.com/k87rte/brainAGE/assets/138688681/400387cb-749e-4c8a-84fa-b6e593a741e7)

# brainAGE
The aging process of our brain is a topic of great significance, as it holds implications for both our physical and mental well-being. Thanks to advancements in medical technology, such as magnetic resonance imaging (MRI), we now have the ability to scan our brains and employ sophisticated methodologies and statistical analyses to estimate their age. This estimation, known as brainAGE, serves as a valuable biomarker of brain health by revealing how the age of our brain differs from our chronological age. By harnessing these cutting-edge techniques, we gain a deeper understanding of the intricate dynamics involved in brain aging, ultimately aiding in the pursuit of enhanced well-being and cognitive vitality. 

## Materials
We will use the 3D MRI-database (https://brain-development.org/ixi-dataset/ free to download). In particular, we are interested in the T1-weighted MRI dataset, as it yields a better image segmentation in comparison to other MRI sequences (datasets), such as T2-weighted and proton density images. Having said that, one can also make use of multispectral image segmentation (combining different MRI images e.g., T1w + proton density).

## Methods
At first, we will segment the images from all the participants. Different brains are different in shapes and sizes. This results in different feature lengths per participant. Hence, the images need to be normalised to a standard space to maintain consistency within features across participants. Later, guassian smoothing is applied with a full width at half maximum of 4mm, to improve signal-to-noise ration. Now the processed images will be scaled using a standrd scalar. We will perform principal component analyses (PCA) to reduce the feature dimensions into explainable orthogonal latent variables. Finally, we will use machine learning (linear regression with regularization - Ridge) to predict chronological age using the latent variables.

## Results
Overall, we found that the model based on gray matter volume derived from 3D MRI-datasets predicts age with a mean absolute error of 7.04 years. The total number of latent variables used are 20. 

## Discussion
Several crucial aspects need to be taken into account in this scenario. Firstly, although the model's validation employs a nested cross-validation approach, the performance of the model on external validation remains unknown. Secondly, the scaling and derivation of latent components were conducted on the entire dataset. This procedure carries the risk of leakage, as the training dataset in each cross-validation fold is somewhat exposed. Thus, it becomes imperative to integrate scaling and PCA into the model pipeline. However, this step was omitted due to computational constraints, which need to be considered.

I hope we have enjoyed this session of data science. We will try to deliver more predictive models in the future.
