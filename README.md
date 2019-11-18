# PhysiCell_MaBoSS

This project contains code for PhysiCell (based on version 1.6.0), with edits to begin incorporating MaBoSS boolean networks into each cell.

The edits include (or, will include) a new /subcellular directory where we will compile the MaBoSS files (and perhaps build a MaBoSS library):
```
~/git/PhysiCell_MaBoSS/subcellular/MaBoSS/engine/src$ 
```

We start off with a very simple test case consisting of 3 cells that are motile and travel horizontally.
```
~/git/PhysiCell_MaBoSS$ make
...
~/git/PhysiCell_MaBoSS$ bn
...
~/git/PhysiCell_MaBoSS$ cd output
~/git/PhysiCell_MaBoSS/output$ python anim_svg.py 
```
