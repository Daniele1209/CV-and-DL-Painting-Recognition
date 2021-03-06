# CV-and-DL-Painting-Recognition

# Team members:

Bumbu Paul
Creta Florin
Borodi Cristian
Mos Daniele
GITHUB REPOSITORY:
https://github.com/Daniele1209/CV-and-DL-Painting-Recognition

## Abstract:

Extensive digitization efforts in the recent years have led to a large increase of digitized and online available fine-art collections. With digitization of artworks, we aim to preserve all those valuable evidences of various human creative expressions, as well as make them available to a broader audience. The digitalization process of artworks should not constrain only to fulfilling the purpose of preservation, but also serve as a starting point for exploring of this type of data in a novel way, which is made possible with the rise of new achievements in computer vision. In the domain of computer analysis of visual art there are various ongoing research challenges. In this project we are going to see how such technologies can be used in order to recognize the artist from a certain painting

## 1. Articles and research papers:

There have been many other articles tackling classification on paintings regarding, genre, artist, painting description and even painting generation using generative adversarial networks. One of the articles that caught our attention was "**Genre Classification of Paintings**" ([https://www.vcl.fer.hr/papers_pdf/Genre Classification of Paintings.pdf](https://www.vcl.fer.hr/papers_pdf/Genre%20Classification%20of%20Paintings.pdf)). It uses feature extraction on paintings using convolutional neural networks, having a dataset from Wiki-Art containing over 1000 images of paintings, that are tagged with the genre corresponding to the painting 

Another good example of such an article is "**Painting-91: a large scale database for computational painting categorization**" ([https://www.diva-portal.org/smash/get/diva2:756963/FULLTEXT01.pdf](https://www.diva-portal.org/smash/get/diva2:756963/FULLTEXT01.pdf)), which uses a dataset consisting of 4266 images of 91 artists and classifies paintings with respect to a certain style of art. It also uses dense sampling scheme for Feature Detection and color-LBP for artist and style classification

We also have an example of style recognition from artworks "**Recognizing Art Style Automatically with deep learning** ([https://www.researchgate.net/publication/331246867_Recognizing_Art_Style_Automatically_with_deep_learning](https://www.researchgate.net/publication/331246867_Recognizing_Art_Style_Automatically_with_deep_learning)), which also uses the Wiki-Art dataset and residual neural network to improve accuracy (> 62%)

## 2. Data:

There are multiple suitable dataset for the problem at hand, such as the painting dataset from the [Rijksmuseum](https://www.rijksmuseum.nl/en) museum, which is a well documented and complex dataset providing mode than 10000 paintings and characteristics, the museum providing an API [1] containing multiple details such as: image, title, complete title, colors, details and many more. This is a totally valid dataset for such a problem, but it might be too complex for the data that we need in order to build the model.

Another good example of dataset would be the Wiki-Art: Visual Art Encyclopedia ****dataset [2] containing around 100k paintings gathered from Wiki-Art, high quality images, also containing tags. Unfortunately the tags in the dataset refer to the "style" of the paintings.

The dataset that we decided to go with is "**Best Artworks of All Time**"  from Kaggle [3] representing a collection of artworks of the 50 most influential artists of all time, which contains the artworks of the most well known artists (50 of them). The dataset contains around 17k different paintings corresponding to 50 artists, each artist having various other characteristics in the csv file, such as the time period, genre, bio and nationality.

## 3. Introduction section:

Computer analysis of visual art, especially paintings, is an interesting cross-disciplinary research domain.
With the spread of digitalization of art paintings,  research on diverse scientific approaches on painted images has become active.
The artistic style (or artistic movement) of a painting is a rich descriptor that captures both visual and historical information about the painting. 
Correctly identifying the artistic style of a painting is crucial for indexing large artistic databases.
Our aim is to investigate the use of deep learning to solve the problem of detecting the artistic style of a painting.

## 4. **Modelling and Training**:

We used a CNN-based approach, with a pre-trained `ResNet50` model (there exist many other approaches to this kind of problem but `ResNet50` gave the best results in our case).

`Imagenet` provided us with pre-trained weights which came in handy. 

Each artist has its representative style which is reflected in each painting using different painting techniques. So we would want to identify the style of the painting corresponding to each artist. 

we are using an ImageDataGenerator from TensorFlow to handle and augment the data (with attributes like rescaling and flipping), then we are splitting the data into training and validation data. The validation data will be used in order to quantify the prediction accuracy. 

When we are fitting the data we are using the validation data as the validation_data argument, training for n epochs, and using the weights calculated earlier. We calculate the weights using the sum of all the paintings divided by the multiplication of the total number of and the number of paintings corresponding to each artist.

# References and Notes:

1. Rijksmuseum dataset and API, data collected since 1885 URL: https://data.rijksmuseum.nl/
2. Wiki-Art dataset, containing tags for the style of paintings URL: https://www.kaggle.com/ipythonx/wikiartgangogh-creating-art-gan
3. Best artworks of all time, Kaggle, collected from artchallenge.ru at the end of February 2019 URL:
https://www.kaggle.com/ikarus777/best-artworks-of-all-time