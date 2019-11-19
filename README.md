# PhysiCell_MaBoSS

This project contains code for PhysiCell (based on version 1.6.0), with edits to begin incorporating MaBoSS boolean networks into each cell.

The edits include (or, will include) a new `/subcellular` directory where we will compile the MaBoSS files (and perhaps build a MaBoSS library):
```
~/git/PhysiCell_MaBoSS/subcellular/MaBoSS/engine/src$ 
```
* additions to `class Molecular` in `/core/PhysiCell_phenotype.h` with the MaBoSS/boolean network model for a cell.
* additions `/core/PhysiCell_cell_container.cpp` where the subcellular model is solved.
* additions `/custom_modules/<custom_code>.cpp` where the subcellular model is referenced by each cell.

On Windows/MinGW, I build MaBoSS in a Command Prompt shell:
```
C:\Users\heiland\git\PhysiCell_MaBoSS\subcellular\MaBoSS\engine\src>make
make -f Makefile.maboss init
make[1]: Entering directory `/c/Users/heiland/git/PhysiCell_MaBoSS/subcellular/MaBoSS/engine/src'
make[1]: Leaving directory `/c/Users/heiland/git/PhysiCell_MaBoSS/subcellular/MaBoSS/engine/src'
make -f Makefile.maboss depend
make[1]: Entering directory `/c/Users/heiland/git/PhysiCell_MaBoSS/subcellular/MaBoSS/engine/src'
make[1]: Leaving directory `/c/Users/heiland/git/PhysiCell_MaBoSS/subcellular/MaBoSS/engine/src'
make -f Makefile.maboss all
make[1]: Entering directory `/c/Users/heiland/git/PhysiCell_MaBoSS/subcellular/MaBoSS/engine/src'
g++ -O2 -Wall -DMAXNODES=64 -std=c++11   -c MaBoSS.cc -o MaBoSS.o
MaBoSS.cc: In function 'int main(int, char**)':
MaBoSS.cc:302:23: warning: 'start_time' may be used uninitialized in this function [-Wmaybe-uninitialized]
     runconfig->display(network, start_time, end_time, mabest, *output_run);
     ~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
MaBoSS.cc:302:23: warning: 'end_time' may be used uninitialized in this function [-Wmaybe-uninitialized]
g++ -O2 -Wall -DMAXNODES=64 -std=c++11   -c MaBEstEngine.cc -o MaBEstEngine.o
g++ -O2 -Wall -DMAXNODES=64 -std=c++11   -c Cumulator.cc -o Cumulator.o
g++ -O2 -Wall -DMAXNODES=64 -std=c++11   -c ProbaDist.cc -o ProbaDist.o
g++ -O2 -Wall -DMAXNODES=64 -std=c++11   -c BooleanNetwork.cc -o BooleanNetwork.o
g++ -O2 -Wall -DMAXNODES=64 -std=c++11   -c BooleanGrammar.cc -o BooleanGrammar.o
g++ -O2 -Wall -DMAXNODES=64 -std=c++11   -c RunConfigGrammar.cc -o RunConfigGrammar.o
g++ -O2 -Wall -DMAXNODES=64 -std=c++11   -c RunConfig.cc -o RunConfig.o
g++ -O2 -Wall -DMAXNODES=64 -std=c++11   -c LogicalExprGen.cc -o LogicalExprGen.o
g++ -o MaBoSS MaBoSS.o MaBEstEngine.o Cumulator.o ProbaDist.o BooleanNetwork.o BooleanGrammar.o RunConfigGrammar.o RunConfig.o LogicalExprGen.o -lpthread
make[1]: Leaving directory `/c/Users/heiland/git/PhysiCell_MaBoSS/subcellular/MaBoSS/engine/src'

C:\Users\heiland\git\PhysiCell_MaBoSS\subcellular\MaBoSS\engine\src>
```


Currently, the PhysiCell "model" defined in `/custom_modules/custom_bn*` is a simple functional test case of just 3 cells that are motile and travel horizontally. It is what we used for an earlier SBML (of ODEs) subcellular model.
```
~/git/PhysiCell_MaBoSS$ make
...
~/git/PhysiCell_MaBoSS$ bn
...
~/git/PhysiCell_MaBoSS$ cd output
~/git/PhysiCell_MaBoSS/output$ python anim_svg.py 
```
