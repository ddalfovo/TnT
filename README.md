# TnT

This is a fork of the Marlin-Na/TnT repository modified to use in a specific application; Some modifications are specific for the specific purpose of the shiny app in which TnT is used, others are purely graphical improvements.

[![Bioc](http://www.bioconductor.org/shields/years-in-bioc/TnT.svg)](https://www.bioconductor.org/packages/devel/bioc/html/TnT.html#since)
[![Travis-CI Build Status](https://travis-ci.org/Marlin-Na/TnT.svg?branch=master)](https://travis-ci.org/Marlin-Na/TnT)
[![Bioconductor Release](https://www.bioconductor.org/shields/build/release/bioc/TnT.svg)](http://bioconductor.org/checkResults/release/bioc-LATEST/TnT/)
[![Bioconductor Devel](https://www.bioconductor.org/shields/build/devel/bioc/TnT.svg)](http://bioconductor.org/checkResults/devel/bioc-LATEST/TnT/)


TnT is a R package that wraps the [TnT javascript libraries](https://github.com/tntvis)
to provide track-based visulizations from R.
It is useful for displaying genomic features as a simple genome browser, particularly
when working with relevant Bioconductor packages.


## Modification

### Genomic coordinates

Three new variables have been created (using Shiny.onInputChange() function) in javasript code to update the genomic coordinates in R code. When the genomic window is moved, zoomed or loaded the three variables are updated and also the shiny app can update this values.

- input$chr
- input$positionStart
- input$positionEnd


### Tooltip
The tooltips generated clicking on a region are disable. Instead a variable is created (using Shiny.onInputChange() function) in javascript to be manipolated and printed in R as DataTable.

- input$tooltipTable


### Track name

The track name is moved up to avoid the overlap between the track name itself and the (block)tracks. The track name 'enter' into the render space of the track above. Usually if you are rendering a list of tracks this is not a problem, but for the first track or other type of track (e.g. a track after a pintrack) have their track name overlapping . To resolve the issue, you can just resolve adding an empty track with a fixed (5px) heigth before this track; or better writing the code in which a empty track of 5px is always added before each track. Each track name will take place within the empty track above.


### TnT render box

Every type of tracks were rendering too wide and the right vertical line of the box was partially overlap by the tracks.