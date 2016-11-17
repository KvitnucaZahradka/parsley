---
layout: post
title:  "Lazy Ions Application"
date:   2016-11-14 11:04:44 -0400
categories: jekyll update
permalink: /welcome/
---
# Application 

This is the blog-post about the application called `lazy ions`. The 
temporary web-page could be found [here]. The aim of the `lazy ions` is 
to analyse the future trendsetters for the new papers released on the 
[arXiv]. 

I am using the Ada - Boosted classifier trained on the set of trendsetter
vs. non-trendsetter papers and metadata downloaded from [arXiv]. The trendsetters 
are defined as the most cited authors in the period of last five years in 
certain area of research. The non-trendsetters are the authors that are 
not trendsetters but are still producing papers in given field.

My application `lazy ions` so far works only for `hep-th` field on arXiv.
I the future other areas will be included as well. You can check `lazy ions` 
code on [github].

The `hep-th` papers predicted to be trendsetters by my application:

1. [paper 1]
2. [paper 2]
3. [paper 3]
4. [paper 4]
5. [paper 5]
6. [paper 6]

# Application details

The whole project is developed in PyCharm in conjunction with live script
run in Jupyther. The project consists of four main steps:

1. Getting raw data from arXiv
2. Exploratory analysis
3. Feature engineering, feature selection and Model building
4. Model evaluation and prediction

I addressed the points **`1.`** to **`4.`** by creating the [Python module]. The module
consists of five classes:

1. class **Data** 
2. class **GetLatestData**  
3. class **Document**
4. class **Learn**
5. class **Predict**

The following diagram describes the interactions between classes and between classes
and environment.

<img src="https://kvitnucazahradka.github.io/parsley/pictures/lazy_ions_diagram.JPG" alt="SF GG" width="555px" >


## Exploratory analysis
In my exploration I looked at various preliminary measures of trendsetting
and non trendsetting papers. One interesting observation was that the 
_Dale-Chall_ readability of "trendsetting" papers is quite different than 
 the readability of "non-trendsetting" papers. I got the following distributions
 of readabilities:

For trending papers:
<img src="https://kvitnucazahradka.github.io/parsley/pictures/trendDaleChall.JPG" alt="SF GG" width="555px" >

For non-trending papers:
<img src="https://kvitnucazahradka.github.io/parsley/pictures/trendDaleChall_notTrending.JPG" alt="SF GG" width="555px" >

## Feature engineering, feature selection and Model building

Having downloaded the meta-data and actual pdf files from arXiv for trendsetters
and non-trendsetters. I split the trendsetting papers to the papers belonging to 
the top trendsetting authors (the upper five per-cent). I call that set **a golden standard**.
I have done that to have base to which I can calculate the **[cosine similarities]** of the 
rest of the papers to the **golden standard**. By this I engineered the global feature for each article. Moreover for each 
paper I calculated the local features (meaning related to the paper itself regardless the corpus). 
The following summarises all features calculated for each paper. By selecting following
features I wanted to catch the formal structure together with factual structure
of papers:

1. [cosine similarities] to the **golden standard**
2. equal sign densities of text
3. equal sign densities of abstract
4. Dale-Chall readabilities of text
5. Dale-Chall readabilities of abstract
6. number of lines density of text
7. number of lines density of abstract
8. length of the text
9. length of the abstract
10. pure text density of text
11. pure text density of abstract

Note, by pure text density ((num. of words in pure text / (num. of words in the orig. text))) I mean 
the density of cleaned up text (text consisting only of factual information nouns). 


## Model evaluation and prediction
The aim of this project was to train the classifier. I picked the Ada-Boosted 
classifier. The reason was that I still had not enormously huge data set. 
So, in this project the scalability was not an issue. The Ada-Boost is considered
the best **out of box** classifier. The [creators] got  **Gödel Prize** for this algorithm.

Moreover I used this algorithm before in the work for the medical startup REVON.

I trained the [scikit-learn] version of the Ada_Boost classifier with a grid search.
I split my data into three groups **training** (70 per-cent) **testing** (20 per-cent)
**validation** (10 per-cent). 

After training I got the classifier with accuracy on validation set to be around 67 per-cent. 
By that classifier I predicted the papers whose links you can find at the 
top of the website. The prediction has been made on the most recent `hep-th` papers 
from arXiv.

## Future work proposal

For the future work I propose the following:

1. Get more data with precise number of citations for each paper
2. More model space exploration
2. Extend the algorithm for different (other than `hep-th`) arXiv sections
3. Extend the algorithm for other media (other than arXiv)
4. Introduce the online learning, with proper implementation of exploration vs. exploitation
5. Personalised version
6. Use the algorithm as trendsetting-nes estimator for authors


[here]: https://glacial-basin-33701.herokuapp.com/about
[arXiv]: https://arxiv.org
[github]: https://github.com/KvitnucaZahradka/LAZY_IONS/blob/master/Document.py
[Python module]: https://github.com/KvitnucaZahradka/LAZY_IONS/blob/master/Document.py
[cosine similarities]: https://en.wikipedia.org/wiki/Cosine_similarity
[creators]: https://en.wikipedia.org/wiki/AdaBoost
[scikit-learn]: http://scikit-learn.org/stable/ 

[paper 1]: https://arxiv.org/abs/hep-th/9108012v1
[paper 2]: https://arxiv.org/abs/hep-th/9108012v1
[paper 3]: https://arxiv.org/abs/hep-th/9108003v1
[paper 4]: https://arxiv.org/abs/hep-th/9108013v1
[paper 5]: https://arxiv.org/abs/hep-th/9109006v2
[paper 6]: https://arxiv.org/abs/hep-th/9109027v1