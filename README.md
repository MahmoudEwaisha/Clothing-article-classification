# Clothing Article Classification

## Dataset:
The dataset used can be found on kaggle through the following [link](https://www.kaggle.com/paramaggarwal/fashion-product-images-dataset). After downloading, extract into fashion_dataset directory.
The dataset contains 44,441 images and different types of annotations. Dataset preparation and insights can be found in the data_preparation.ipynb notebook.

## Experiments:
- ### Resnet50:
   First, we experiment with resnet-50 as a baseline. The documented code and steps can be found in resnet-50.ipynb. (also experimented with other networks but no big difference in results)

- ### Custom Model:
   Although starting from a pretrained model usually yields bettwe results than training from scratch, I think the problem/current data is not so hard to train a new model on. The final custom model can be found in Custom_Network.ipynb along with MACs/FLOPS calculation and receptive field analysis.

&nbsp;

## Areas for improvement:
- Depending on the dataset (and the task required), more than one item of clothing can be present in an image (images of people for example not separate clothing articles) which can yield wrong results when compared to a single ground truth label. This can be handled differently depending on the requirements. This can be handled by returning and computing results based on topk predictions as done in DeepFashion (and using topk accuracy as a metric instead). Another approach would be to formulate the problem as:
   - A multilable classification (person wearing jeans, shirt, classic shoes, etc) 
   - An object detection problem where we detect different clothing items and classify each one accordingly.
- Experiment with different computationally efficient backbones (like mobilenet) pretrained on a relevant dataset or on Imagenet.
- Use different dataset. DeepFashion dataset has more images & labels types which can be used to make a more robust model. I initially wanted to use this dataset but had constant problems downloading it.

