---
title: "Creating Interactive Collapsible Tree Diagrams in R using D3.js"
date: "2017-03-28"
---

A few weeks ago, I was working on a [Shiny](https://shiny.rstudio.com/) app that would interface with our database, allowing you to pick out a section or subsection of data and visualize your selection. The trouble was, it was tough to see the forest for the trees using a series of linked drop-down lists. You could successfully narrow down a dataset using this method, but it wasn't very friendly or appealing, nor would it lend you any perspective as to where in the hierarchy your selection was.

The first thing I did was check out the [htmlwidgets gallery](http://gallery.htmlwidgets.org). The [networkD3](http://christophergandrud.github.io/networkD3/) package seemed promising, but it took me over an hour to get my data frame formatted into the proper list structure that D3 wanted. If you're working with R, you're used to data frames, not JSON structures.

I came across the [data.tree](https://cran.r-project.org/web/packages/data.tree/vignettes/data.tree.html) package, which is a powerful tool for creating and manipulating hierarchal lists. I put together a little script to turn a data frame into a list and added that to my Shiny app, alongside networkD3.

The tree diagram was a bit too crowded with all of the nodes shown at the same time, so I searched around for examples, when I came across Mike Bostock's [collapsible tree example](https://bl.ocks.org/mbostock/4339083). This is perfect! I added a JavaScript dependency to my Shiny app and added an `.on('click')` function that would phone home to Shiny with the most recently clicked node. This allowed me to eliminate the need for drop-down lists and use the tree diagram as my select input.

I found myself reusing this pattern in a couple of other visualizations and interactions, and thought it might be useful to a few other people as well, so I wrapped it up into an htmlwidget! This was my first time building an R package or an htmlwidget, but thankfully there's plenty of [good reading material](http://r-pkgs.had.co.nz/)  to help point you in the right direction.

If you're interested, you can find `collapsibleTree` on [CRAN](https://cran.r-project.org/package=collapsibleTree) and [GitHub](https://github.com/AdeelK93/collapsibleTree).
