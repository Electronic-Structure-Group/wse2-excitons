# Band structure and excitonic properties of WSe<sub>2</sub> in the isolated monolayer limit in an all-electron approach

This GitHub repository hosts the data files and related information for the research paper titled "Band structure and excitonic properties of WSe<sub>2</sub> in the isolated  monolayer limit in an all-electron approach," authored by Niloufar Dadkhah and Walter R. L. Lambrecht, available on arXiv:2402.17924

## Repository Structure

The repository is structured to provide easy access to the data files used in the figures of the paper. Below is a guide to the contents and organization:

### 1. Grace Files (Folder: `agr`)
- **Description**: Contains `.agr` for use with [XMGRACE](https://plasma-gate.weizmann.ac.il/Grace/).
- **Figures Covered**: 2, 3, 4, 5.
  
| Figure     | agr file |
| ------------- |-----|
| Fig. 2      | fig2.ag |
| Fig. 3      | fig3.agr     |
| Fig. 4      | fig4.agr     |
| Fig. 5      | fig5.agr    |

### 2. VESTA Files (Folder: `vesta`)
- **Description**: Includes vesta file format for visualization with [VESTA](https://jp-minerals.org/vesta/en/).
- **Figure Covered**: 8, 9.
  
| Exciton label   | vesta file         |
| --------------- | -----------------  |
| &lambda;= 1,2   | xcfh-w-1and2.vesta  |
| &lambda;= 3     | xcfh-w-3.vesta       |
| &lambda;= 4     | xcfh-w-4.vesta      |
| &lambda;= 5,6   | xcfh-w-5and6.vesta   |
| &lambda;= 7,8   | xcfh-w-7and8.vesta   |
| &lambda;= 21,22 | xcfh-w-21and22.vesta |
- **Features**: Enables users to explore the structure and exciton wavefunction data from various angles and at different sections and adjust isosurface values for exciton distributions.

### 3. Band Structure Data (Folder: `bnds`)
- **Description**: Contains ASCII files with band structure data relevant to figures 1 and 6.
- **Data Format**: Information on the number of bands, Fermi level, k-point labels, and energy eigenvalues. Details at [Questaal Data Format](https://www.questaal.org/docs/input/data_format/#bnds-file).

```line 1: number of bands, Fermi level, k-point labels
line 2: number of points long first line
line 3: k-point coordinates in units 2pi/a  with a the lattice constant
lines 4 -40: energy eigenvalues  in Rydberg
line 5: next k-point followed by bands etc.
until end of line.
```
- **Visualization**: Data can be visualized using [Questaal's plbnds tool](https://www.questaal.org/docs/misc/plbnds/) or band-plot.py (included).
- **Files Included**: `bnds.lda`, `bnds.rpa`, `bnds.bsw` (representing different computational approximations).
 | Approximation  | file |
| ------------- |:-----:|
| LDA   | bnds.blue |
| QSGW     | bnds.red |
| QSGW$\hat$     | bnds.green |



### 4. Meta Data 
- **Description**: Provides the fundamental input files (`ctrl.wse` and `site.wse`) needed to generate all the dataset, alongside `.rst`, `syml`, and `sigm` files for the self-consistent potential restart data and the self-energy files.

<!Organization: Data is arranged in subfolders for the bulk and various `c` values, facilitating quick regeneration of the results.>


### 5. h5 Files (Folder: `h5`)
- **Description**: Contains `.h5` files to use for k-space visualiations of excitons.
- **Figures Covered**: 6, 8.
- **Files Included**:
     
     - w2q0e.h5 contains three data sets related to the two-particle BSE Hamiltonian.
      The dimensions of the BSE Hamiltonian is determined by:
        
        - 1- number of k-points used for the BSE calculation (specified by nkgw1, nkgw2, nkgw3 for three directions)
        - 2- number of valence bands (nv) and conduction bands (nc) used for the BSE calculation.
        - 3- number of spins (nspin). If the calculation is spin-polarized, nspin=2, else nspin=1.
    
     Then the number of eigenvectors (nw) and length of each eigenvector (lw) will be:.
  
         $-nw=lw=nkgw1*nkgw2*nkgw3*nv*nc$

     Three data sets in w2q0e.h5 file are:
        
     _Two-particle BSE Hamiltonian eigenenergies known as the exciton energies (ew):_
       
       ew      Dataset {nspin, nw}
      
    
     _Oscillator strength for each excitonic energies:_
    
       rccr    Dataset {nq, nw}
       
      where nq is the number q-vector directions for which the oscillator strengths are calculated. By default the directions are (1,0,0) (0,1,0) (0,0,1) (1,1,1)
     
    _Eigenvectors associated which each eigenenergy (w)_
    
       w       Dataset {nspin, nw, lw}
       
       which are written in the row-major order.

  - bz.h5 k-point mesh data.


## Additional Information

For more details on the paper and the corresponding research findings, please refer to the [arXiv publication](#).

This repository aims to support the reproducibility of our research by providing comprehensive datasets and tools necessary for analysis. We encourage the use of these resources in academic and research settings.
