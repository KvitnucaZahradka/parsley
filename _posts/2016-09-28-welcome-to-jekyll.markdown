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

I addressed the points `1.` to `4.` by creating the Python module. The module
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
and non trendsetting papers. I found that 



[here]: https://glacial-basin-33701.herokuapp.com/about
[arXiv]: https://arxiv.org
[github]: https://github.com/KvitnucaZahradka/LAZY_IONS/blob/master/Document.py

[paper 1]: https://arxiv.org/abs/hep-th/9108012v1
[paper 2]: https://arxiv.org/abs/hep-th/9108012v1
[paper 3]: https://arxiv.org/abs/hep-th/9108003v1
[paper 4]: https://arxiv.org/abs/hep-th/9108013v1
[paper 5]: https://arxiv.org/abs/hep-th/9109006v2
[paper 6]: https://arxiv.org/abs/hep-th/9109027v1