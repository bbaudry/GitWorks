Peacock collaboration visualization
===================================
We aim at visualizing the collaboration dynamics of a fork tree in a github repository.
A fork tree consists of all forks of the same repository (for instance the 1159 forks of [ACE](https://github.com/ajaxorg/ace).
We focus on the "commit flows" between the forks and the root of the fork tree (the "main" repository of the fork tree). The resulting visualization of large fork trees often looks like a "peacock" tail.
![Peacock collaboration visualization for ACE](/images/ace.png)

Explanation
---------------
We use a circle-based visualization.  A peacock picture includes three main elements, each of them displaying information about a repository.

![Peacock legend](/images/peacock-legend.png)

###The main circle 

The main circle is divided in stripes, that we call **fork-stripe**s. Each fork-stripe represents a fork in the repository. There are two types of fork-stripes:
* *the largest fork-stripe* at the bottom of the picture. This fork-stripe represents the main fork. Its size is equal to the total number of commits that are shared between the main fork and any other fork.
* *all other fork-stripes*. Each fork-stripe represents a fork that has at least one commit in common with the main fork. All these stripes are ordered, clockwise starting from the left of the main fork, according to the creation date of the fork. The size of each fork-stripe is equal to the number of commits the fork has in common with the main fork. The color of the fork is proportional to the number of commits the fork has in common with the main fork.
Because of the very large numbers of forks and commits in some projects, we vizualize only the forks that have at least one commit in common with the main fork.

###Ribbons inside the main circle 

There is one ribbon, called a **commit flow** between the main fork-stripe and each other fork-stripe. The width of a commit flow between the main fork and another fork *F* is equal to the number iCommits in *F*.
A iCommit is a commit that is present in the main fork of a repository and in one and only one other fork
The color of the commit flow is also proportional to the number iCommits in *F* (over the maximum number of iCommits that appear in a single fork of the project).
 

###Outer circles

Some fork-stripes have a circle on their outer edge. This circle, called a **UC-circle**, represents the number of unique commits (uCommits) in the fork. A uCommit is a commit that is present in a single fork of the project The size of a UC-circle is equal to the number of unique commits in the fork and its color is proportional to the number of unique commits in the fork (over the total number of unique commits)

The  color of each colored element of the ribbons (commit flow  and UC-circles) is selected in a 350 colors gradient that goes from  white to red, and that contains the colors of a rainbow. 

Collaboration Models
---------------------

Vizualizing commit flows in different repositories allowed us to observe different collaboration models.

### "Goose" collaboration model
In the goose model, the main fork is forked multiple times. However, the contribution of each fork to the main is very unbalanced: a few forks contribute a lot, while most of the others contribute little. ACE is an example of that model. The peacock visualization highlights the lack of balance through the colors of the commit-flows: in the ACE peacock, three commit-flows have colors that are very different from the others (which means that they contribute a much higher proportion of the commits than the others).

### "Chick" collaboration model
In the chick model, the main fork is forked only a few times. [pysynergy](https://github.com/emanuelez/PySynergy) is an example of this model.
![Chick collaboration visualization for PySynergy](/images/PySynergy.png)
    
### "Seabirds" collaboration model
In the seabird model, the main fork is forked multiple times. In this model, the contribution of each fork to the main is balanced: many forks contribute equally. [zamboni](https://github.com/mozilla/zamboni)  is an example of that model. The peacock visualization highlights the balance through the colors of the commit-flows: many commit-flows have similar colors, indicating an equivalent proportion of commits contributed to the main fork.
![Seabirds collaboration visualization for zamboni](/images/zamboni.png)
### "Galapagos" Effect (Speciation)
The galapos model emphasizes the presence of some forks that have many uCommits. Our intuition is that many uCommits indicate a speciation inside a fork, probably one or several branches that are used to develop alternative solutions that are not shared with the other forks. [pyromcs](https://github.com/pyrocms/pyrocms) is an example in which the main fork has a very large UC-circle 
![Galapagos collaboration visualization for pyrocms](/images/pyrocms.png)
##Data and Tools
The data have been collected by [marbiaz](https://github.com/marbiaz), [monperrus](https://github.com/monperrus) and [bbaudry](https://github.com/bbaudry) from github. 
We have collected data about forks, authors and commits from 108 repositories that have more than 2 forks. Then we classified commits according to their type (iCommit, uCommit and other types that we do not visualize here). This data was then visualized with [circos](http://circos.ca/ "Circos"). The code to produce the peacocks is available in  [this project](GitWorks/src/ "source code").
