GitWorks
========

The data have been collected and the images have been synthesized by Marco Biazzini, Martin Monperrus and Benoit Baudry

##Intention

The pictures presented in this project have two main intentions:

* capture a single, global view on a project that is hosted on GitHub

* vizualize the dynamics of commits among all the forks of a project

For each project, we identify a main fork, and we focus on two specific kinds of commits that we define below:

<dl>
  <dt>iCommit</dt>
  <dd>An iCommit is a commit that is present in the main fork of a project and in one and only one other fork</dd>
  <dt>uCommit</dt>
  <dd>A uCommit is a commit that is present in one single fork of the project</dd>
</dl>

##Pictures

Each picture captures a global view on a project that is hosted on GitHub. 

A picture includes three main elements, each of them displaying information about a project

###The main circle 

The main circle is divided in stripes, that we call **fork-stripe**s. Each fork-stripe represents a fork in the project. There are two types of fork-stripes:

* *the largest fork-stripe* on the left side of the picture. This fork-stripe represents the main fork. Its size is equal to the total number of commits that are shared between the main fork and any other fork

* *all other fork-stripes*. Each fork-stripe represents a fork that has at least one commit in common with the main fork. All these stripes are ordered, clockwise, according to the creation date of the fork. The size of each fork-stripe is equal to the number of commits the fork has in common with the main fork. The color of the fork is proportional to the number of commits the fork has in common with the main fork.

Each fork-stripe is composed of inner stripes, called **author-bands** that represent the authors that contributed to a fork. The color of an author-band is proportional to the number of commits the author contributed to the fork (over the maximum number of commits represented in the fork-stripe)

###Ribbons inside the main circle 

There is one ribbon, called a **commit-link** between the main fork-stripe and each other fork-stripe. The width of a commit-link between the main fork and another fork *F* is equal to the number iCommits in *F*; the color of the commit-link is proportional to the number iCommits in *F* (over the maximum number of iCommits that appear in a single fork of the project).

###Outer circles

Some fork-stripes have a circle on their outer edge. This circle called a **UC-circle** represents the number of unique commits in the fork. The size of a UC-circle is equal to the number of unique commits in the fork and its color is proportional to the number of unique commits in the fork (over the total number of unique commits)


###Coloring algorithm

The color of each colored element (fork-stripes, author-bands, commit-links and UC-circles) is selected in a 350 colors gradient that goes from white to red, and that contains the colors of a rainbow. When an element has a color that is proportional, *e.g.*, to the number of commits, 

###Vizualization tool


Pictures are generated with [circos](http://circos.ca/ "Circos")

##Data collection

Because of the very large numbers of forks and commits in projects, we have to select subsets that will be vizualized.


