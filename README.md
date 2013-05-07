Peacock collaboration visualization
===================================
We aim at visualizing the collaboration dynamics of a fork tree in a github repository.
A fork tree consists of all forks of the same repository (for instance the 1159 forks of [ACE](https://github.com/ajaxorg/ace).
We focus on the "commit flows" between the forks and the root of the fork tree (the "main" repository of the fork tree). The resulting visualization of large fork trees often looks like a "peacock" tail.
![Peacock collaboration visualization for ACE](/images/ace.png)

Explanation
---------------
We use a circle-based visualization.  A peacock picture includes three main elements, each of them displaying information about a repository.

![Peacock legend](/images/peacock-legend.jpg)

###The main circle 

The main circle is divided in stripes, that we call **fork-stripe**s. Each fork-stripe represents a fork in the project. There are two types of fork-stripes:
* *the largest fork-stripe* at the bottom of the picture. This fork-stripe represents the main fork. Its size is equal to the total number of commits that are shared between the main fork and any other fork.
* *all other fork-stripes*. Each fork-stripe represents a fork that has at least one commit in common with the main fork. All these stripes are ordered, clockwise starting from the left of the main fork, according to the creation date of the fork. The size of each fork-stripe is equal to the number of commits the fork has in common with the main fork. The color of the fork is proportional to the number of commits the fork has in common with the main fork.
Because of the very large numbers of forks and commits in some projects, only the main ones are visualized (*e.g.*, 652/1159 forks for ACE).

###Ribbons inside the main circle 

There is one ribbon, called a **commit flow** between the main fork-stripe and each other fork-stripe. The width of a commit flow between the main fork and another fork *F* is equal to the number iCommits in *F*.
A iCommit is a commit that is present in the root fork of a reposiroty and in one and only one other fork
The color of the commit flow is also proportional to the number iCommits in *F* (over the maximum number of iCommits that appear in a single fork of the project).
 

###Outer circles

Some fork-stripes have a circle on their outer edge. This circle called a **UC-circle** represents the number of unique commits (uCommits)in the fork. A uCommit is a commit that is present in a single fork of the project The size of a UC-circle is equal to the number of unique commits in the fork and its color is proportional to the number of unique commits in the fork (over the total number of unique commits)

The  color of each colored element of the ribbons (commit flow  and UC-circles) is selected in a 350 colors gradient that goes from  white to red, and that contains the colors of a rainbow. 

Collaboration Models
--------------------------------------
### "???" collaboration model
Many forks, unbalanced commit flow.
This is ACE
### "Chick" collaboration model
A few authors having their own forks:
![Chick collaboration visualization for PySynergy](/images/PySynergy.png)
    
### "Seabirds" collaboration model
Many authors contribute with comparable shares
Goose in V which alternate
See 
![Seabirds collaboration visualization for zamboni](/images/zamboni.png)
### "Galapagos" Effect (Speciation)
pyromcs
could be speciation within the main fork (use of branch?)
within other forks
![Galapagos collaboration visualization for pyrocms](/images/pyrocms.png)
##Data and Tools
The data have been collected by marbiaz, monperrus and bbaudry. 
Pictures are generated with [circos](http://circos.ca/ "Circos")
