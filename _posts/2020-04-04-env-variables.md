---
title: Environment Variables and Package Management using Anaconda
---

Hola Folks Welcome.

So if you are here your today’s read is on Python’s Package Management System and Virtual Environment, thanks for showing interest now sit right back, hold your cup of coffee and keep that pack of snacks 5 meters apart, because this is going to be short and for the period we don’t want any disturbance.

First things First, the target audience specifically for this blog are the people with no prior development experience and transition to
Data Science, Machine Learning or AI,  and use Anaconda in Windows, if you are one, then bud this is the right place in by the end of this
blog you will have a lot in your head and hand to try hands-on.
From General Perspective it is for everyone who uses Anaconda in Windows for Development.
 
So my friend, a couple of days ago my other friend who is a student of Bachelor of Commerce and not so much aware with the development
aspect of programming, recently got into the field of Data Science and Machine learning, he told me that he was having severe panic attacks
understanding the concepts of Package Management System and Virtual Environment, without adieu I told him [“Corey Schafer ”](https://coreyms.com/) the start and 
the end for Python Development, however, having already boggled a lot over youtube videos he didn’t want to stargaze for more, to be quick
in time he asked me to explain the same.

Here’s what I told him in the easiest of language I could ever speak :
Virtual Environment: A virtual environment is an isolated working copy of Python which allows you to 
work on a specific project without worry of affecting other projects. It enables multiple side by side
installations of python one for each project. It’s is just a clever way of isolating the dependencies
and requirements for each project.
To make things simpler I used Dodo the Duck for those of you who don’t know anything about Dodo, he is an imaginary friend of mine, I often use for explaining things, Fun Fact: he knows programming better than me and sometimes and is fond of Electronic Dance Music.

So suppose Dodo was working on a project that used Python 3 but now his boss told him to work coherently on the second project that needs python 2, now every time he needs to switch between his work, it won’t be convenient for him to Uninstall his Python Version and Reinstall the one according to his usage.But Dodo is smart he makes use of Virtual Environment and creates two different Virtual Environment, one for the project using Python 3 and the other for the project that uses Python 2.
This way his dependencies do not overlap, projects remain isolated and workflow becomes easy.
Now that we have understood about Virtual Environment Let’s understand Python's Package Management System.
Package Management: Before delving deeper into Package Management we should first understand what a package is, so no diplomacy keeping things simple Numpy is a package, Matplotlib is a package, Pandas is Package by definition a package is a collection of python modules wherein a module is a single python file.
So essentially and automatically Package management means being able to handle the packages effectively.
Now, most of the python packages are stacked up at the Python Package Index (PyPI) and can be installed by making use of Package Managers, ‘pip’ is one of the most popular.

That's a lot of reading and I hope you haven’t forgotten about my friend and now that he had understood about the theory behind all these he was already having the feels of wings but he wanted more, he wanted to Fly so he asked me for hands-on and here’s how I demonstrated it.

Since a lot of people who get direct exposure to Data Science without any prior experience of Development use Anaconda, so I shall explain how to do it in Anaconda.
So Anaconda once installed comes with its Package Management System and Environment Management System called Conda.
Anaconda once installed although contains pretty much all of the Packages used in Data Science and Machine Learning.
To use Anaconda effectively with Dev-Vibes all you need to do is navigate to your ```Anaconda Prompt``` and:

1) To access easy guide on Conda Commands type:
```
conda --help
```
2) To check the packages installed with Anaconda use :
```
conda list
```
3) To install a new Package  use :
```
conda install numpy
```
4) To install multiple packages say “numpy ,scipy,pandas” use:
```
conda install numpy scipy pandas
```
5) To install a package with a specific version use:
```
conda install  numpy=1.2
```
6) To search about all the available versions of a package or you are unaware of the exact package name so you can use:
```
conda search *numpy*
```
7) To update a Package use:
```
conda update numpy
```
8) To update all Packages present in anaconda use:
```
conda update -–all
```
9) To remove a package use:
```
conda remove numpy
```
*P.S: All the above commands have been used regarding numpy, and can be performed with any package by replacing ‘numpy’ with any other package.*

For me, these 9 commands have pretty much worked out more than enough in every scenario.
Now let's talk about Virtual Environment.
Just like I told you before Conda is the ultimate Super cool Dude and more than the other half of ANA-CONDA , it manages the virtual environment of it effectively and efficiently.By default, Anaconda comes up with an environment called ‘base’ and initially in Anaconda your Presence in Base Environment looks like this.

-------------------------------------------------------

1) Now to create a new Environment say ‘my_app’ where my_app is my Environment name for a project for my python app, all you need to type is :

```
conda create --name my_app
```
2) Once the Environment has been created, to enter in its use:
```
conda activate my_app
```
Once it has been activated and you enter into the environment it will be indicated as :
--------------------------------------------------------
3) The packages can be installed similarly and the rest of the Package Management remains the same as described in the Package Management part, except for the fact that packages installed in this environment are closely isolated to the specific environment.

4) To fetch the environments being created using:
```
conda env list
```
5) Once the Environment is created and all the dependencies have been installed and the project is done, to mark a check on the version of dependencies used in the project, the environment can be exported to a yml file as:
```
Conda env export> environment.yaml
```
The ```environment.yaml``` file so contains all the information of the packages and version stacked up all together in one place.

6) To create an Environment from a yml file use:
```
Conda env create –f environment.yaml
```
7) Once the work is done to quit the Environment use:
```
Conda deactivate
```
8) Once the whole Project is Done you might want to remove the environment, to do so use:
```
Conda env remove –n my_app
```
*P.S: All the commands have been used regarding Dummy Environment ‘my_app’ and can be replaced with the environment you want to create.*

That’s all a few commands and a basic understanding and you are ready for your neat development.
That being said, allow me to leave for the day and if you got any queries please do not hesitate to reach out.
Thank you and Happy Learning.


