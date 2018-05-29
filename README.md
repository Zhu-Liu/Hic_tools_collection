# A collection of tools for Hi-C data analysis

Slowly growing as notes from my Zotero collection are getting organized.

## Reviews

- Waldispühl, Jérôme, Eric Zhang, Alexander Butyaev, Elena Nazarova, and Yan Cyr. “Storage, Visualization, and Navigation of 3D Genomics Data.” Methods, May 2018. https://doi.org/10.1016/j.ymeth.2018.05.008. - Review of tools for visualization of 3C-Hi-C data, challenges, analysis (Table 1). Data formats (hic, cool, BUTLR, ccmap). Database to quickly access 3D data. Details of each visualization tool in Section 4

- A list of tools available for data analysis and/or visualization of 4DN-related datasets. https://www.4dnucleome.org/software.html

- Ay, Ferhat, and William S. Noble. “Analysis Methods for Studying the 3D Architecture of the Genome.” Genome Biology 16 (September 2, 2015): 183. https://doi.org/10.1186/s13059-015-0745-7. - Hi-C technology and methods review. [Table 1](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-015-0745-7#Tab1) - list of tools. Biases, normalization, matrix balancing. Extracting significant contacts, obs/exp ratio, parametric (powerlaw, neg binomial, double exponential), non-parametric (splines). 3D enrichment. References. TAD identification, directionality index. Outlook, importance of comparative analysis

- Forcato, Mattia, Chiara Nicoletti, Koustav Pal, Carmen Maria Livi, Francesco Ferrari, and Silvio Bicciato. “Comparison of Computational Methods for Hi-C Data Analysis.” Nature Methods, June 12, 2017. https://doi.org/10.1038/nmeth.4325. - Hi-C processing and TAD calling tools benchmarking, [Table 1](https://www.nature.com/articles/nmeth.4325/tables/1), simulated (Lun and Smyth method) and real data. Notes about pluses and minuses of each tool. TAD reproducibility is higher than chromatin interactions, increases with larger number of reads. Consistent enrichment of TAD boundaries in CTCF, irrespectively of TAD caller. Hi-C replication is poor, just a bit more than random. Supplementary table 2 - technical details about each program, Supplementary Note 1 - Hi-C preprocessing tools, Supplementary Note 2 - TAD callers. Supplementary note 3 - how to simulate Hi-C data. Supplementary note 6 - how to install tools. https://images.nature.com/full/nature-assets/nmeth/journal/v14/n7/extref/nmeth.4325-S1.pdf

- Nicoletti, Chiara, Mattia Forcato, and Silvio Bicciato. “Computational Methods for Analyzing Genome-Wide Chromosome Conformation Capture Data.” Current Opinion in Biotechnology 54 (December 2018): 98–105. https://doi.org/10.1016/j.copbio.2018.01.023. - 3C-Hi-C tools review, Table 1 lists categorizes main tools, Figure 1 displays all steps in technology and analysis (alignment, resolution, normalization, including accounting for CNVs, A/B compartments, TAD detection, visualization). Concise description of all tools.



## Multi-purpose

- `HiCExplorer` - set of programs to process, normalize, analyze and visualize Hi-C data, Python. https://hicexplorer.readthedocs.io/en/latest/, https://github.com/deeptools/HiCExplorer/

- `hiclib` - tools to qc, map, normalize, filter and analyze Hi-C data, https://bitbucket.org/mirnylab/hiclib

- `my5C` tools - well-documented analysis and visualization of 5S data, http://my5c.umassmed.edu/

## QC

- `3DChromatin_ReplicateQC` - Comparison of four Hi-C reproducibility assessment tools, `HiCRep`, `GenomeDISCO`, `HiC-Spector`, `QuASAR-Rep`. Tested the effects of noise, sparsity, resolution. Spearman doesn't work well. All tools performed similarly, worsening expectedly. QuASAR has QC tool measuring the level of noise. https://github.com/kundajelab/3DChromatin_ReplicateQC
    - Yardimci, Galip, Hakan Ozadam, Michael E.G. Sauria, Oana Ursu, Koon-Kiu Yan, Tao Yang, Abhijit Chakraborty, et al. “Measuring the Reproducibility and Quality of Hi-C Data,” September 14, 2017. doi:10.1101/188755. 

- `HiC-Spector` - reproducibility metric to quantify the similarity between contact maps using spectral decomposition. Decomposing Laplacian matrices and sum the Euclidean distance between eigenvectors. https://github.com/gersteinlab/HiC-spector
    - Yan, Koon-Kiu, Galip Gürkan Yardimci, Chengfei Yan, William S. Noble, and Mark Gerstein. “HiC-Spector: A Matrix Library for Spectral and Reproducibility Analysis of Hi-C Contact Maps.” Bioinformatics (Oxford, England) 33, no. 14 (July 15, 2017): 2199–2201. https://doi.org/10.1093/bioinformatics/btx152.



## Visualization

- `HiTC` - import, normalize, annotate and visualize Hi-C data, https://bioconductor.org/packages/release/bioc/html/HiTC.html and https://www.bioconductor.org/packages/devel/bioc/vignettes/HiTC/inst/doc/HiTC.pdf

- `pyGenomeTracks` - Standalone program and library to plot beautiful genome browser tracks. https://github.com/deeptools/pyGenomeTracks

- "Genome contact map explorer" gcMapExplorer - analyze and compare Hi-C contact maps, plot other data types alongside. Normalization: KR, IC, and their distance-centric normalization MCFS (median contact frequency). HDF5 file format for fast data access, LZF compression. Python3. Command line and GUI versions. https://rjdkmr.github.io/gcMapExplorer/, https://gcmapexplorer.readthedocs.io/en/latest/. Rajendra Kumar et al., “Genome Contact Map Explorer: A Platform for the Comparison, Interactive Visualization and Analysis of Genome Contact Maps,” Nucleic Acids Research 45, no. 17 (September 29, 2017): e152–e152, https://doi.org/10.1093/nar/gkx644.



## Normalization

- `HiCNorm` - removing biases in Hi-C data via Poisson regression, http://www.people.fas.harvard.edu/~junliu/HiCNorm/

- `caICB` - chromosome-adjusted iterative correction of biases method. Review of Hi-C data biases and methods to remove them. CNV bias cannot be removed after within-chromosome iterative correction bias methods. The distance-dependent decay of interaction frequencies is modeled by splines. The caICB method aims to minimize the differences across count-distance curves of different chromosomes, chr1 as the reference. A priori knowledge of CNVs is not required. The between- and within-chromosome bias is removed, minimizing the number of significant contacts due to CNVs. https://bitbucket.org/mthjwu/hicapp
    - Wu, Hua-Jun, and Franziska Michor. “A Computational Strategy to Adjust for Copy Number in Tumor Hi-C Data.” Bioinformatics (Oxford, England) 32, no. 24 (15 2016): 3695–3701. https://doi.org/10.1093/bioinformatics/btw540.

- `OneD` - CNV bias-correction method, addresses the problem of partial aneuploidy. Bin-centric counts are modeled using negative binomial distribution, and its parameters are estimated using splines. A hidden Markov model is fit to infer copy number for each bin. Each Hi-C matrix entry is corrected by dividing its value by square root of the product of CNVs for the corresponding bins. Reproducibility score (eigenvector decomposition and comparison) to measure improvement in the similarity between replicated Hi-C data. https://github.com/qenvio/dryhic
    - Vidal, Enrique, François le Dily, Javier Quilez, Ralph Stadhouders, Yasmina Cuartero, Thomas Graf, Marc A Marti-Renom, Miguel Beato, and Guillaume J Filion. “OneD: Increasing Reproducibility of Hi-C Samples with Abnormal Karyotypes.” Nucleic Acids Research, January 31, 2018. https://doi.org/10.1093/nar/gky064.


## Interaction callers

- `Fit-Hi-C` - detection of significant chromatin interactions, https://noble.gs.washington.edu/proj/fit-hi-c/


## TAD detection

- `Armatus` - TAD detection at different resolutions, https://www.cs.cmu.edu/~ckingsf/software/armatus/, https://github.com/kingsfordgroup/armatus

- `HiCseg` - TAD detection by maximization of likelihood based block-wise segmentation model, https://cran.r-project.org/web/packages/HiCseg/index.html



## SNP-oriented

- `iRegNet3D` - Integrated Regulatory Network 3D (iRegNet3D) is a high-resolution regulatory network comprised of interfaces of all known transcription factor (TF)-TF, TF-DNA interaction interfaces, as well as chromatin-chromatin interactions and topologically associating domain (TAD) information from different cell lines.  
    - Goal: SNP interpretation
    - Input: One or several SNPs, rsIDs or genomic coordinates.
    - Output: For one or two SNPs, on-screen information of their disease-related info, connection over TF-TF and chromatin interaction networks, and whether they interact in 3D and located within TADs. For multiple SNPs, same info downloadable as text files.


## Prediction

- 3DEpiLoop - prediction of 3D interactions from 1D epigenomic profiles using Random Forest trained on CTCF peaks (histone modifications are the most important predictors, and TFBSs). https://bitbucket.org/4dnucleome/3depiloop
    - Al Bkhetan, Ziad, and Dariusz Plewczynski. “Three-Dimensional Epigenome Statistical Model: Genome-Wide Chromatin Looping Prediction.” Scientific Reports 8, no. 1 (December 2018). https://doi.org/10.1038/s41598-018-23276-8.


## Misc

- `HiCPlus` - increasing resolution of Hi-C data using convolutional neural network. Basically, smoothing parts of Hi-C image, then binning into smaller parts. Performs better than bilinear/biqubic smoothing. https://github.com/zhangyan32/HiCPlus
    - Zhang, Yan, Lin An, Ming Hu, Jijun Tang, and Feng Yue. “HiCPlus: Resolution Enhancement of Hi-C Interaction Heatmap,” March 1, 2017. https://doi.org/10.1101/112631.



