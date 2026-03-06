# ML Screening of High-Entropy Alloy Catalysts for Nitrogen Reduction

### Overview
This project aims to advance research in the burgeoning materials science subfield of high-entropy alloys (HEAs) for catalysis by leveraging machine
learning techniques, namely a random forest regressor, to forecast how well computer-generated HEAs theoretically enable nitrogen reduction reactions (NRR). Improving the efficiency of NRRs is of interest because they may primarily be used for the eco-friendly, ambient-condition production of ammonia for fertilizers, displacing the carbon-intensive Haber-Bosch process. Additionally, this ammonia acts as a potential carbon-neutral hydrogen carrier, enabling safe, energy-dense storage and transportation for fuel cells. 

### Methodology
First, a random sampling of 4-6 element HEAs was generated from the AlloySustainability-supported element pool and featurized with Magpie elemental
descriptors in Matminer. Then, a random forest regressor from Scikit-learn was trained on N* adsorption energies from a dataset from Mamun et al. (2019),
pulled via Catalysis-Hub GraphQL API. Generated candidate materials were screened and only included if -1.5 < ΔGN < 0.5 eV, then ranked by proximity to
the optimal -0.25 eV (both range and optimal value sourced from Skúlason et al. 2019). Finally, AlloySustainability (Gorsse et al., 2024) was used to score each candidate on nine metrics about environmental safety and supply chain risk, among others, and more filtering was conducted *post hoc*. 

### Usage
All code runs in Google Colab. Open `hea_notebook.ipynb` and run cells sequentially.

### Assumptions and Limitations
This model is trained on bimetallic surface data from Mamun et al. (2019) and applied to predict N* adsorption energies on 4-6 element HEA compositions. This extrapolation assumes that composition-averaged elemental descriptors (Magpie features) capture sufficient information about surface electronic structure to generalize from binary to higher-order alloys and is supported by prior work showing reasonable transferability of composition-based models to HEA surfaces (Batchelor et al., Joule 2019; Pedersen et al., ACS Catalysis 2020). It is consistent with a mean-field treatment of HEA surfaces in which local site environments are treated as statistical samples of the bulk composition. Predictions should be interpreted as composition-level screening estimates rather than precise site-specific adsorption energies, and top candidates are intended for further validation by site-resolved methods.

## References
- Mamun et al., *High-throughput calculations of catalytic properties 
  of bimetallic alloy surfaces*, Sci. Data (2019)
- Gorsse et al., *Considering sustainability when searching for new 
  high entropy alloys*, Sust. Mat. Tech. (2024)
- Batchelor et al., *High-Entropy Alloys as a Discovery Platform for 
  Electrocatalysis*, Joule (2019)
- Skúlason et al., *A theoretical evaluation of possible transition
  metal electro-catalysts for N2 reduction*, Phys. Chem. Chem. Phys., 
  2012.
## Author
Thomas M. Finan, University of Missouri, 2026
