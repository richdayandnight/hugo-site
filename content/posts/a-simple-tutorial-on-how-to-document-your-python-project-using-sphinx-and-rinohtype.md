+++
cover = ""
date = ""
draft = true
linktitle = "A Simple Tutorial on How to document your Python Project using Sphinx and Rinohtype"
series = []
tags = ["Python", "Sphinx"]
title = "A Simple Tutorial on How to document your Python Project using Sphinx and Rinohtype"
type = []
weight = ""
[author]
name = "Rich Yap"

+++
# A Simple Tutorial on How to document your Python Project using Sphinx and Rinohtype

> Documenting code is one of the tasks I really don’t want to do, but I’ll do it for the grades anyway.

This is probably what you’ll hear from me when I was a first year computer science student. I found documenting code boring and useless as I already know what my code does and the only person who’ll probably read it is the professor checking it.

I didn’t understand its importance until one day, I needed to look at that undocumented code I wrote years ago for reference and instead of just skimming through it, I spent a lot of time being quite confused about how I structured the project and even how to run it.

Today, there are a lot of tools available to help us in documenting code. Recently, I learned of tools that make it easy to create intelligent and beautiful documentation. Two of those are Sphinx and Rinohtype.

Sphinx, written by Georg Brandl and licensed under the BSD license, was originally created for [the Python documentation](https://docs.python.org/) and it has excellent facilities for the documentation of software projects in a range of languages (Sphinx-doc.org, 2018).

Rinohtype, paired with Sphinx offers a modern alternative to [LaTeX](http://en.wikipedia.org/wiki/LaTeX) . It provides a Sphinx backend that allows generating professionally typeset PDF documents (Machiels).

### In this tutorial, I’ll be using Sphinx and Rinohtype to produce an HTML and PDF documentation files respectively to a simple API project I wrote that manages a list of Teacher records ([Github Project Link](https://github.com/richdayandnight/Tutorial_SimpleTeacherAPI)) .

1. Clone the project and delete/move the docs folder so you may follow me in creating the new documentation.
2. Go to the root directory of the project.
3. Create and activate a Python 3 virtual environment

   virtualenv -p python3 <name of virtualenv>
   source <name of virtualenv>/bin/activate

![Here I named my virtual environment ‘venv’](https://cdn-images-1.medium.com/max/2000/1*G__9z51DfI7pqHnm9rFWBA.png)_Here I named my virtual environment ‘venv’_

1. Install all the project requirements

   pip install -r requirements.txt

Note: Sphinx and Rinohtype are already inside the requirements.txt file. If you wish to install them in the virtual environment of the project you’re working on use the following commands below.

    pip install Sphinx
    pip install rinohtype

1. Create a docs directory and **cd** into this directory.

   mkdir docs
   cd docs
2. Setup Sphinx

   sphinx-quickstart

![Follow this configuration for now. You may reconfigure this later on your own.](https://cdn-images-1.medium.com/max/2000/1*3GeKx7mfbRMkEatvUjL-Yw.png)_Follow this configuration for now. You may reconfigure this later on your own._

![continuation of the previous picture](https://cdn-images-1.medium.com/max/2000/1*hJU9QaPV1ColEG9SIc98Yg.png)_continuation of the previous picture_

1. Open source/conf.py

* Configure path to root directory

![Uncomment lines 15–17](https://cdn-images-1.medium.com/max/2000/1*toYP5LpVVDBGwm8Q2Rt2GQ.png)_Uncomment lines 15–17_

![Change path to ‘../..’ and Add sys.setrecursionlimit(1500)](https://cdn-images-1.medium.com/max/2000/1*SZYb2_6_GEkhNjYJer_qkg.png)_Change path to ‘../..’ and Add sys.setrecursionlimit(1500)_

The path should point to the root directory of the project and looking at the project structure, from conf.py we should reach the root by going up two parent directories.

![Project structure](https://cdn-images-1.medium.com/max/2000/1*OlJexT1WRuXWltzXRfy1Ug.png)_Project structure_

* Add Rinohtype to the list of extension

  'rinoh.frontend.sphinx'
* Uncomment the latex elements

![uncomment these](https://cdn-images-1.medium.com/max/2000/1*fApTWXZJphDDoqbRMPbB7A.png)_uncomment these_

![You can change the format further, these are just the default.](https://cdn-images-1.medium.com/max/2000/1*i4PY7uooztxvKmZLSv_baQ.png)_You can change the format further, these are just the default._

1. Open the [index.rst](https://github.com/richdayandnight/Tutorial_SimpleTeacherAPI/blob/master/docs/source/index.rst) and change the content to the following. (Click the index.rst link for full content)

   Documentation for the Code

   ***

       
       .. **toctree:: :maxdepth:** 2 **:caption:** Contents:
       
       # TeacherAPI main
       
       .. **automodule::** app **:members:
       
       # **TeacherAPI controller
       
       .. **automodule::** teacherAPI.controller **:members:
       
       # **TeacherAPI models
       
       .. **automodule::** teacherAPI.models **:members:
       
       # **TeacherAPI database
       
       .. **automodule::** teacherAPI.database **:members:
       
       # **TeacherAPI populate
       
       .. **automodule::** teacherAPI.populate **:members:**
       
2. Create the HTML and PDF documentation files.

* Still inside the docs directory run

  make html
  sphinx-build -b rinoh source _build/rinoh

EDIT NOTE \[March 16, 2019\]: Building the pdf file would fail if your Python version is ≥3.7.0 ([Github issue reference](https://github.com/brechtm/rinohtype/issues/133))

**_The first line would produce the HTML file in docs/build/html/index.html_**

![View of index.html](https://cdn-images-1.medium.com/max/2082/1*MbbTf-xJw7-vp476DuNP1w.png)_View of index.html_

![View of index.html](https://cdn-images-1.medium.com/max/2078/1*K2SXOVXrzrraG2YveCGd9A.png)_View of index.html_

**_The second line would produce the PDF file in docs/_build/rinoh/SimpleTeacherDataAPI.pdf_**

![Title page of the documentation](https://cdn-images-1.medium.com/max/2000/1*d1ZaYtu8NrOzRkTqFjwwoA.png)_Title page of the documentation_

![Table of contents](https://cdn-images-1.medium.com/max/2000/1*6dhDi7thA5VwQC2STdMNgQ.png)_Table of contents_

![Sample page of the documentation](https://cdn-images-1.medium.com/max/2000/1*p048sQvD_IK9il7se02VWQ.png)_Sample page of the documentation_

After experiencing being in team projects, I began developing appreciation in documenting code and even though, I wouldn’t say it’s the most enjoying task, it’s definitely reliable and should be practiced by programmers <_Looking at you self_>.

![](https://cdn-images-1.medium.com/max/2000/1*aKxfrwQhexd9gsYWiBHFJw.jpeg)

To learn more about Sphinx:

* [Overview — Sphinx 1.8.0+ documentation](http://www.sphinx-doc.org/en/master/)

Other useful tutorials:

* [Documenting Your Project Using Sphinx](https://pythonhosted.org/an_example_pypi_project/sphinx.html) — This helped me in understanding how to document my code using Python docstrings.
* [Brandon’s Sphinx Tutorial](https://media.readthedocs.org/pdf/brandons-sphinx-tutorial/latest/brandons-sphinx-tutorial.pdf) — Extensive tutorial on using Sphinx

Machiels, Brecht. “Rinohtype: The Python Document Processor — Rinohtype 0.3.1.Dev0 Documentation.” _Rinohtype.readthedocs.io_. N.p., 2016. Web. 17 June 2018.

Sphinx-doc.org. (2018). _Overview — Sphinx 1.8.0+ documentation_. \[online\] Available at: [http://www.sphinx-doc.org/en/master/](http://www.sphinx-doc.org/en/master/) \[Accessed 17 Jun. 2018\].

***

This article is cross-posted @ [Medium](https://medium.com/@richdayandnight/a-simple-tutorial-on-how-to-document-your-python-project-using-sphinx-and-rinohtype-177c22a15b5b)