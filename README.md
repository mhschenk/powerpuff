## About Us

The Powerpuff Girls are a team of students from Brown University's DATA 2040 Class: Amanda Khoo, Laura McCallion, and Marie Schenk. Follow our progress through our midterm project assignment here!


## First Entry - February 18, 2020

Hello! Welcome to our blog, which will detail our progress through our midterm project for the class DATA 2040 at Brown University. The project is the [Kaggle competition](https://www.kaggle.com/c/bengaliai-cv19) to classify handwritten graphemes of the Bengali language. As explained on the competition homepage, a grapheme is the smallest unit of a written language. Graphemes represent individual sounds in the words of a language Bengali has 18 accents (or diacritics)  that can be added to its 49 letters. The combination of diacritic and letter makes up a grapheme. Therefore, Bengali has many more graphemes than English does, and the task of identifying and classifying handwritten Bengali graphemes is more complicated than in English. If you're interested in understanding more about the Bengali alphabet, we recommend [these slides](https://bengali.ai/wp-content/uploads/CV19-COCO-Grapheme.pdf) and [this website](http://www.lingvozone.com/Bengali). 

Like many in the class, we have started with [this notebook,](https://www.kaggle.com/kaushal2896/bengali-graphemes-starter-eda-multi-output-cnn) which was suggested to us by our TA. Today, we will give you a look at the data we are working with and our early thoughts for the construction of our classification model.

Because there are so many graphemes in Bengali, it's infeasible to look at all possible graphemes that might ultimately come through our model. Here are some statistics on the most common graphemes in our dataset. 

The top ten roots in the training set are:

|index      | component | count |
|-----------|-----------|-------|
|   72      |    দ      |   5736|
|64 |       ত |  5596 |
|13 |         ক |   5420 |
|107 |         ব |   5321 |
|23 |         গ |   5149 |
|96 |         প |   4926 |
|113 |         ভ |   4395 |
|147 |         স |   4392 |
|133 |         শ |   4374 |
|115 |         ম |   4015 |

The bottom ten roots in the training set are:

|index | component |  count |
|----|----|----|
|73  |  দ্ঘ |    130 |
|33  |  ঙ্ক্ত |    136 |
|102 |  প্স |   141 |
|158 |  স্স |    143 |
|45  |  জ্জ্ব |    144 |
|130 |  ল্ব |   144 |
|1   | ঃ |    145 |
|12  |  ঔ |    146 |
|0   |   ং |    147 |
|63  |  ণ্ণ |    149 |

As you can see, there are many fewer examples of these bottom ten roots than the top ten. We expect that our model will do better on the components with more examples. This is something for us to consider as we start getting results. 

The top five vowels in the training dataset (not including the diacritics that could be added) are:

|index | component|  count|
|---|---|---|
|168 |         0 |  41508 |
|169 |         া |  36886 |
|175 |         ে |  28723 |
|170 |         ি |  25967 |
|172 |         ু |  18848 |

The top five consonents present in the training dataset are:

|index | component |   count|
|---|---|---|
|179 |         0 |  125278 |
|181 |        র্ |   23465 |
|184 |        ্র |   21397 |
|183 |        ্য |   21270 |
|180 |         ঁ |    7424 |


### Early Results

Thus far, we have run the model on four different subsets of training data. These graphs indicate that we should focus especially on increasing the accuracy of the model's classification of roots, as those consistently score the lowest across the different datasets. 

<img src="graph0L.png">

<img src="graph0A.png">

<img src="graph1L.png">

<img src="graph1A.png">

<img src="graph2L.png">

<img src="graph2A.png">

<img src="graph3L.png">

<img src="graph3A.png">

### Next Steps
For the subsequent steps of our project, we will focus on improving the performance of this notebook. We can adjust training time (number of iterations), examine for over- or under-fitting, and adjust various aspects of the model architecture in order to find potential improvements. We also plan on examining the techniques used in the most effective models based on the best scoring kaggle notebooks, and potentially adapt them for use in our base model. 

Stay tuned for further updates as we continue working on this project!

## Second Entry - March 3, 2020

Welcome back! We've taken several steps to improve and refine our model, which we discuss below.

### Augmenting Data

One of the most fundamental ways to improve the performance of a neural net model is to train it on more data. The more data a model has seen, the more precisely it can estimate parameters and the better it can handle new, unseen data. We've taken a similar approach to other teams who have publicly posted their notebooks on Kaggle, which is to augment our data with altered versions of the existing images. We've added Gaussian noise, rotated the images left and right, and heightened the clarity. Examples of these modifications are shown below. The original source for these modifications is [this notebook on Kaggle]("https://www.kaggle.com/chekoduadarsh/bengali-ai-understand-and-augment-eda"). We wrote our own function to apply the modifications to a subset of the training data and create a new dataframe.

Here is an image with Gaussian noise added. The background and character are no longer just two separate colors.

<img src = "gaussian noise.png">

Here is an image rotated to the right...

<img src = "rotate right.png">

...and one rotated to the left.

<img src = "rotate left.png">

An image with the intensity changed to make the character more clear:

<img src = "change intensity.png">


## Third Entry - March 3, 2020

Our model is now complete! This entry serves to explain the performance of our final model. We've added a couple extra layers. Below you can find our new architecture.

We got our new results by changing the architecture slightly and tuning hyper parameters using kerastuner (link). Our final performance is as follows:

