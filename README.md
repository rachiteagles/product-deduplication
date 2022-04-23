# product deduplication

The goal of this project was to identify similar products listed on any e-commerce website using the image of the product and its description.

E-commerce websites have products that are sold by multiple sellers. Each seller can upload different images and descriptions of the same product. These images and descriptions can be highly diverse. Identifying these duplicates is essential to improve user experience as well as to optimize resources. The goal of this project is to identify duplicated products among ~33k products sold by multiple sellers on Shopee.

As the dataset has more than ~11k distinct class labels of products,multiclass classification model wasn’t feasible. The solution implemneted is based on finding similar products(deduplication) by different approach of vector embeddings of products. To achieve this, Transfer Learning was implemented in which images were initially converted to embeddings using pretrained model like VGG-11 and Resnet. A model was then trained on these embeddings to classify them as same or different

**Datasets used**

We use a combination of 2 sources to obtain this data:

  - Kaggle Shopee competition data
    - ~ 32500 observations

  - Data scraped from ebay
    - ~ 6000 observations

Each observation has 	

  - Each observation has the following attributes:
    - Image (1000 x 1000 RGB image)
    - Product description
    - Label Group (unique product ID)
    - Posting ID (unique observation ID)
    - Image pHash

**Dataset**

<img src="images/Dataset.png" width="50%">

The images and descriptions shown here all belong to the same product

<img src="images/data_image.png" width="50%">
<img src="images/data_text.png" width="50%">

**Modelling Approach**

Make meaningful vector representations of each product. This is achieved by using
   - Embeddings of title text
     - TFIDF
     - RoBERTa (Multilingual)

   - Embeddings of image
     - ResNet18

     Joint Embeddings (text + image)

