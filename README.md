## About Us

The Powerpuff Girls are a team of students from Brown University's DATA 2040 Class: Amanda Khoo, Laura McCallion, and Marie Schenk. Follow our progress through our midterm project assignment here!


## First Entry - February 18, 2020

Hello! Welcome to our blog, which will detail our progress through our midterm project for the class DATA 2040 at Brown University. The project is the [Kaggle competition](https://www.kaggle.com/c/bengaliai-cv19) to classify handwritten graphemes of the Bengali language. As explained on the competition homepage, a grapheme is the smallest unit of a written language. Graphemes represent individual sounds in the words of a language Bengali has 18 accents (or diacritics)  that can be added to its 49 letters. The combination of diacritic and letter makes up a grapheme. Therefore, Bengali has many more graphemes than English does, and the task of identifying and classifying handwritten Bengali graphemes is more complicated than in English. If you're interested in understanding more about the Bengali alphabet, we recommend [these slides](https://bengali.ai/wp-content/uploads/CV19-COCO-Grapheme.pdf) and [this website](http://www.lingvozone.com/Bengali). 

Like many in the class, we have started with [this notebook,](https://www.kaggle.com/kaushal2896/bengali-graphemes-starter-eda-multi-output-cnn) which was suggested to us by our TA. Today, we will give you a look at the data we are working with and our early thoughts for the construction of our classification model.

Because there are so many graphemes in Bengali, it's infeasible to look at all possible graphemes that might ultimately come through our model. Here are some statistics on the most common graphemes in our dataset. 

\begin{tabular}{lrlr}
\toprule
{} &  index & component &  count \\
\midrule
72  &     72 &         দ &   5736 \\
64  &     64 &         ত &   5596 \\
13  &     13 &         ক &   5420 \\
107 &    107 &         ব &   5321 \\
23  &     23 &         গ &   5149 \\
96  &     96 &         প &   4926 \\
113 &    113 &         ভ &   4395 \\
147 &    147 &         স &   4392 \\
133 &    133 &         শ &   4374 \\
115 &    115 &         ম &   4015 \\
\bottomrule
\end{tabular}
