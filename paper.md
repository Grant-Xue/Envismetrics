---
title: 'Envismetrics: A Python-based software for electrochemical kinetic analysis'
tags:
  - Python
  - electrochemistry
  - kinetic analysis
  - online software
  - data analysis
authors:
  - name: Huize Xue
    orcid: 0000-0001-7537-2173
    affiliation: "1"
    equal-contrib: true
  - name: Wenbo Wang
    orcid: 0000-0002-0784-7509
    affiliation: "2"
  - name: Xinxin Zhou
    orcid: 0009-0001-0960-6688
    affiliation: "3"
  - name: Fuqin Zhou
    orcid: 0009-0000-0342-0033
    affiliation: "4"
  - name: Omowunmi Sadik
    orcid: 0000-0000-0000-0000
    corresponding: true
    affiliation: "5"
affiliations:
 - name: New Jersey Institute of Technology, Department of Physics
   index: 1
 - name: New Jersey Institute of Technology, Department of Informatics
   index: 2
 - name: Independent Researcher
   index: 3
 - name: New Jersey Institute of Technology, Chemistry and Environmental Science
   index: 4
 - name: New Jersey Institute of Technology, Chemistry and Environmental Science
   index: 5
date: "2024-08-30"
bibliography: bibliography.bib
---

# Abstract

Envismetrics is an innovative, open-source, and cross-platform Python-based software designed to streamline the electrochemical kinetic analysis process. This software suite offers a comprehensive toolbox for researchers, enabling efficient processing and analysis of electrochemical data from various potentiostats. Key features include data import and processing, advanced peak searching, Randles-Ševčík analysis, rate constant calculation, and Tafel analysis. Envismetrics also provides educational resources to aid users in understanding complex electrochemical concepts and terminologies. By simplifying and automating data analysis, Envismetrics aims to promote reproducibility, transparency, and ease of use in electrochemical research. The code is available at [https://github.com/Woffee/Envismetrics](https://github.com/Woffee/Envismetrics).

# Summary

Accurate determination of kinetic electrochemical parameters and thermodynamic constants is vital for predicting and optimizing the performance of redox reactions in various applications [@SANECKI2003109, @wang2020redox, @XU20106366]. These kinetic parameters can also be used in simulations to understand the mechanisms of the reactions [ @C9CP05527D]. However, many of these parameters are not widely available in existing literature or online databases and often vary depending on experimental conditions.

Cyclic voltammetry (CV), hydrodynamic voltammetry (HDV), and step methods such as chronoamperometry (CA) are widely used experimental techniques to obtain kinetic parameters [@bard2022electrochemical]. These experiments enable the determination of key kinetic parameters through various analyses:

- **Hydrodynamic Voltammetry (HDV)**: Levich and Koutecky-Levich analysis.
- **Cyclic Voltammetry (CV)**: Randles-Sevcik analysis, rate constant calculation, transfer coefficient calculation.
- **Chronoamperometry (CA)**: Cottrell equation analysis.

These analyses help calculate essential kinetic parameters, including formal potential, diffusion coefficient, transfer coefficient, and rate constant. Once collected, these parameters are widely used to perform simulations based on the Butler-Volmer theory, providing further insights into the electrochemical system.

# Statement of Need

In terms of data handling, typical electrochemical kinetic analysis solutions have relied on instrument-specific proprietary software provided with potentiostats, homemade scripts for specific data, or manual processing in Excel. Compared with the proprietary tools available from potentiostat manufacturers, these often lack the flexibility, cross-platform support, and comprehensive functionality that Envismetrics offers. Compared with homegrown solutions and packages [@Garg2021, @Murbach2020], Envismetrics provides a more general function that saves time and eliminates the need to re-edit code when changing potentiostats or experimental methods in kinetic analysis. Users can rely on Envismetrics to streamline their workflow and enhance efficiency. 

Table 1 provides a general comparison between Envismetrics, proprietary tools (using Metrohm NOVA 2.1.7 as an example), and self-developed software (using FuelCell as an example).

Envismetrics provides an open-source, cross-platform (Windows, MacOS, and Linux) online software focused on electrochemical kinetic analysis. No installation or updates are required, making it convenient and always up-to-date. Envismetrics offers a full toolbox for processing raw voltammogram data, extracting parameters, and generating publication-ready figures. The analysis can be applied to any scan, cycle, or range of voltammogram data. At any stage of the analysis, users can export the results for further use or to create new figures. Whether users are professional researchers seeking to save time or individuals lacking basic knowledge of the relevant equations, Envismetrics encourages reproducible, easy-to-use, and transparent analysis.

Envismetrics not only facilitates data collection and analysis from electrochemical experiments but also provides educational resources to help users understand the terminology and concepts they encounter. This dual approach ensures that both seasoned researchers and newcomers can effectively utilize the software.

Envismetrics is dedicated to continuous improvement and innovation. Future plans include incorporating widely used kinetic electrochemical analysis methods and expanding support for additional data formats from various potentiostat brands. The software's modular design enables the seamless integration of new features and methods, ensuring Envismetrics remains a leading tool in electrochemical analysis.


| **Aspect**             | **NOVA**                           | **Envismetrics**                                                                          | **Fuelcell**                                       |
|------------------------|------------------------------------|-------------------------------------------------------------------------------------------|----------------------------------------------------|
| **Installation**        | Windows (7 to 11)                 | Online (no installation, always up-to-date)                                                | Standalone executable                              |
| **Compatibility**       | Autolab instruments               | Cross-platform (Windows, macOS, Linux, no hardware dependence)                             | Cross-platform (Windows, macOS, Linux)             |
| **Data Formats Supported** | Autolab-specific formats        | XLSX, TXT, CSV, versatile for many devices                                                 | Multiple data formats                              |
| **Analysis Tools**      | Smoothing, fitting, peak search   | Dynamic HDV slope, peak search, Randles-Ševčík analysis, rate constant calculation          | Tafel slope, HFR extraction                        |
| **User Interface**      | Complex, detailed                 | User-friendly, drag-and-drop, suitable for all users                                       | Interactive GUI                                    |
| **Learning Curve**      | Steep                             | Intuitive and user-friendly, minimal training required                                     | Simple but limited in advanced functionality        |
| **Customization**       | Requires expertise                | Modular, easy updates, customizable for advanced research                                  | Custom visualizations                              |
| **Updates**             | Periodic, requires installation   | Seamless, online updates, community-supported                                              | Expandable via community                           |
| **Platform Support**    | Windows only                      | Cross-platform                                                                             | Cross-platform                                     |
| **Hardware Support**    | Metrohm Autolab-specific          | Versatile (multiple devices)                                                               | Versatile (multiple devices)                       |
| **Special Features**    | Device integration, extensive tools | Cross-platform versatility, cutting-edge methods, educational resources, advanced analysis modules | Basic GUI, limited to programmatic use for advanced features |
[Comparison of Electrochemical Data Analysis Software]\label{table:1}

# Current Functions of Envismetrics Toolbox

## Data Processing

Envismetrics supports a wide range of data formats from various potentiostats, including EC-Lab, Autolab, Metrohm, and more. The software can handle document types such as XLSX, TXT, and CSV. Users simply need to export their data and drag the files into the software, making data import and processing straightforward and user-friendly. We are continuously adding support for more commonly used commercial potentiostats. If you do not find support for your specific potentiostat, rest assured that updates will be released shortly to include additional data formats.

![Data Import Window: Users can easily drag and drop or select their experimental data for quick and straightforward import.](Image_Set/1.png){ width=80% }

## Hydrodynamic Voltammetry (HDV) Module

### Function 1: Plotting and Gaussian Filtering

This function plots the experimental data sorted by RPM (rotations per minute) values and allows users to apply a Gaussian filter to obtain a smoothed figure. Users can add the optional Gaussian filter by entering the sigma value, enhancing the clarity of the plotted data.

### Function 2: Levich and Koutecky-Levich Analysis

Levich and Koutecky-Levich analyses are essential for calculating the diffusion coefficient [@masa2014koutecky]. Traditionally, this involves selecting several potential values, plotting the function of RPM versus the function of current, performing linear regression, and calculating the diffusion coefficient from the slope.

Envismetrics simplifies this process by providing an automated Levich and Koutecky-Levich plot function. Users can generate these plots directly from their data. Additionally, the software offers an advanced analysis feature that dynamically calculates and records the slope and diffusion coefficient for every applied potential. This allows users to observe the changes in the slope with varying potentials, helping them decide which range of data to select for their analysis.

## Cyclic Voltammetry (CV) Module

### Function 1: Plotting and Gaussian Filtering

This function plots cyclic voltammetry data sorted based on the rate constant value and allows users to apply a Gaussian filter for smoothing. Users can input the sigma value to adjust the degree of smoothing. Both the original figure and the smoothed data will be displayed, allowing users to compare the raw and processed results.

### Function 2: Peak Searching

Peak searching is essential for calculating formal potential, peak separation, and performing Randles-Ševčík analysis. The software provides multiple searching methods, such as max/min and knee/elbow detection within specific ranges, allowing the analysis of multiple peaks and complex reactions. The software will record all the peak points for use in future analyses, and the results will be displayed in a plot.

### Function 3: Randles–Ševčík Analysis

The Randles–Ševčík analysis utilizes equations that incorporate the transfer coefficient and calculate the diffusion coefficient from the peak current and scan rate. This function supports both reversible and irreversible versions of the Randles–Ševčík equation [@zanello2019inorganic]. The peak information data used in this analysis is obtained from Function 2 (Peak Searching):

$$
I_{\text{peak}} = 0.4463 \, n \, F \, C \, A \sqrt{\frac{n F \nu D}{R T}}
$$

$$
I_{\text{peak}} = 0.4463 \sqrt{n^{\prime} + \beta} \, n \, F \, C \, A \sqrt{\frac{n F \nu D}{R T}}
$$

### Function 4: Rate Constant Calculation

The rate constant is calculated using a dimensionless kinetic parameter, \(\Psi\). This parameter is a normalized value that represents the rate constant (\(k_0\)) in relation to various factors such as the diffusion coefficient and the number of electrons transferred. The method is suggested by Nicholson (1965) and Lavagnini et al. (2004) [@nicholson1965theory, @lavagnini2004extended].

### Function 5: Tafel Analysis Module

Tafel analysis is used to determine the anodic and cathodic transfer coefficients. The International Union of Pure and Applied Chemistry (IUPAC) formally defines these coefficients as experimentally determined values, given by [@guidelli2014defining]:

$$
\alpha_a = \frac{RT}{F} \left( \frac{d \ln j_{a, \text{corr}}}{dE} \right)
$$

$$
\alpha_c = -\frac{RT}{F} \left( \frac{d \ln |j_{c, \text{corr}}|}{dE} \right)
$$

Additionally, the mass-transport corrected version suggested by Danlei Li et al. (2018) is used in this module [@LI2018117]. This method has also been applied in other research, such as the study of dopamine oxidation at gold electrodes by Bacil et al. (2019) [@zanello2019inorganic]. The transfer coefficient is calculated by:

$$
-\frac{d\ln \left( \frac{1}{I_a} - \frac{1}{I_{\text{peak}}} \right)}{d\theta} = \alpha_a'
$$

## Step Techniques Structure: CA Module

### Function 1: Plotting and Gaussian Filtering

This function generates plots of applied potential vs. time and corresponding current vs. time. Users have the option to input a sigma value to apply a Gaussian filter, which smooths the data for clearer visualization. Both the original and smoothed figures are displayed, allowing for easy comparison and analysis.

### Function 2: Cottrell Equation Plot

This function utilizes the Cottrell equation to calculate the diffusion coefficient. The Cottrell equation describes the current response of an electrochemical cell as a function of time, providing a means to determine the diffusion coefficient from chronoamperometric data. The software plots the Cottrell equation, allowing users to input parameters such as interval, \( n \), \( A \), and \( C_0 \), and calculates the diffusion coefficient. The outputs include a figure of the Cottrell equation plot and a table of diffusion coefficients.

![(a) Levich plot module](Image_Set/2.png){ width=45% }
![(b) Levich analysis module](Image_Set/3.png){ width=45% }
![(c) Peak Searching module](Image_Set/4.png){ width=45% }
![(d) Randles–Ševčík Analysis Module](Image_Set/RS_analysis.png){ width=45% }

![Example of figures in Envismetrics: (a) Levich plot module, (b) Levich analysis module, (c) Peak Searching module, (d) Randles–Ševčík Analysis Module.]

## Applications in Research

Envismetrics has been employed in various research projects, demonstrating its versatility in the analysis of electrochemical systems. For instance, the software was utilized in the investigation of photocatalytic degradation of perfluorooctanoic acid (PFOA), published in *Chemosphere* [@OSONGA2024143057], where it facilitated the precise analysis of kinetic parameters essential to understanding the degradation mechanisms. Additionally, Envismetrics played a key role in mechanistic studies on the electrochemical oxidation of dimethylamine borane (DMAB), as documented in recent works [@sadik2024dimethylamine, Xue_2023]. In these studies, Envismetrics enabled the accurate processing of electrochemical data, which was crucial for validating the proposed mechanisms and deriving key kinetic parameters.


# Technology Stack

The online platform is primarily built with Python, leveraging the Flask framework. JQuery is employed for real-time features and asynchronous tasks. More details can be found on our GitHub repo.

# Acknowledgments
The authors acknowledge the NJIT Start-ups (172803) and the Bill Melinda Gates Foundation for funding.


# Conflict of Interest
The authors confirm that we have read the JOSS conflict of interest policy, that we have no COIs related to reviewing this work, and that JOSS has waived any perceived COIs for the purpose of this review.

# Code of Conduct
The authors confirm that we read and will adhere to the JOSS code of conduct.

# References
