# Tristan Albatross Satellite Detection Analysis

![Static Badge](https://img.shields.io/badge/python-blue?logo=python&logoColor=yellow)
![GitHub](https://img.shields.io/github/license/ninagw3/Walrus_from_space?color=green)

This repository contains the data and Python script used in the study:
Attard et al. (In review) Feasibility of using very high-resolution satellite imagery to monitor Tristan albatrosses *Diomedea dabbenena* on Gough Island. *Endangered Species Journal.*

The study evaluates the detectability of Tristan Albatrosses in high-resolution WorldView-4 satellite imagery (31 cm resolution) over Gough Island, Tristan da Cunha. The goal is to determine whether satellite imagery can facilitate population monitoring of this critically endangered species during the breeding season.

---

### **Table of Contents**

<!-- TOC -->
* [Introduction](#introduction)
* [Script Overview and Workflow](#script_overview_and_workflow)
* [Installation](#installation)
* [Usage](#usage)
* [Structure](#structure)
* [Results](#results)
    * [GLM minimum age](#GLM-minimum-age)
    * [GLM model comparison](#GLM-model-comparison)
    * [Chi-squared test](#Chi-squared)
    * [Observer performance](#Observer-performance)
    * [Gold standard](#Gold_standard)
    * [Observer clustered data](#Observer-clustered-data)
* [Reusing or Adapting the script](#reusing_adapting_script)
* [Acknowledgements](#acknowledgements)
* [License](#license)
* [Funding](#funding)

<!-- TOC -->

---

## Introduction

The Tristan Albatross *Diomedea dabbenena* is critically endangered, facing threats such as bycatch and predation. Monitoring this species is challenging due to financial constraints and logistical difficulties. Satellite imagery offers a potential solution for cost-effective population monitoring.

This repository includes a Python script that automates the analysis of satellite imagery data to assess the detectability of Tristan Albatrosses. It also generates the figures and tables required for the study.

## Script Overview and Workflow

The Python script processes the data and performs the necessary analysis to determine the visibility and detectability of Tristan Albatrosses in satellite imagery. It uses the input data from the various folders and generates output plots and tables for further analysis.

Script workflow:
1. Loads the necessary data (CSV, XLSX, or JPEG files from the Data folder).
2. Processes the satellite imagery data and field survey nest GPS coordinates.
3. Conducts an analysis to assess albatross detectability based on various predictors.
4. Generates output plots (figures) and tables, which are saved in the output folder.

## Installation
To set up the project:

1. Clone the repository:

bash
git clone https://github.com/your-username/project-name.git
cd project-name
Set up a virtual environment (recommended):

2. Set up a virtual environment (recommended):
bash
python -m venv venv
Install the required dependencies:

3. Install dependencies
bash
pip install -r requirements.txt
If requirements.txt is unavailable, manually install dependencies.

Usage
The script is designed to be run in a Jupyter Notebook environment. Follow these steps:

1. Install JupyterLab:
bash
pip install jupyterlab

2. Launch Jupyter Notebook:
bash
jupyter notebook

3. Run the analysis:

Open Tristan_albatross_satellite_image_detection.ipynb in the python_script folder.
Ensure all input data is correctly placed in the data folder.
Run the cells sequentially to execute the analysis.

## Structure

The project is designed as follows: 

```
Tristan Albatross Satellite Detection Analysis
│
├── Data
│   │  This data provides the input for the python script, comprising of satellite image data, nest coordinates, and volunteer-labelled data. 
│   │  All data for this project is organised into subfolders within the data folder.
│   │
│   ├──Gough_island_landscape_features
│   │       Shapefiles for Gough Island’s landscape features (coastline, ocean, contours, and mountain peaks), extracted from a Digital Terrain Model provided by RSPB with <10 m resolution.
│   │
│   ├──nest_boundaries
│   │       Shapefiles of Tristan Albatross nest boundaries on Gough Island, including Gonydale and the Hummocks, provided by RSPB.
│   │
│   ├──nest_GPS_coordinates
│   │       GPS coordinates of Tristan Albatross nests in cloud-free regions of the satellite image, provided by RSPB for the 2017/18 breeding season. Accurate to 10 m. 
│   │ 
│   ├──nesting_bird_information:
│   │     ├──['Tristan_albatross_age_sex_data.csv'](./data/nesting_bird_information/Tristan_albatross_age_sex_data.csv)
│   │     │   Minimum age and sex of each nesting bird.
│   │     ├──['Tristan_albatross_nest_colony_information.csv'](./data/nesting_bird_information/Tristan_albatross_nest_colony_information.csv)
│   │     │   List of nesting birds detected in the 31 cm orthorectified satellite image (152 nests). This    includes the nest ID and colony the nest is from. 
│   │     └──['Tristan_albatross_nest_location_data.csv']:(./data/nesting_bird_information/Tristan_albatross_nest_colony_information.csv): 
│   │         Slope (degrees) and aspect data of 152 nests extracted from each nest GPS coordinate in ArcGIS Pro using the Digital Elevation Model provided by RSPB.
│   │
│   ├──observer_annotations
│   │        Contains CSV files with raw output from 9 observers using VGG Image Annotator (VIA), which is used for assessing interobserver reliability.
│   │
│   ├──reference_annotations
│   │       Contains CSV files and point shapefiles of reference 1 (Initials: MRGA) and reference 2 (Initials: PC) annotations of presumed Tristan albatrosses in all cloud-free regions of the satellite image.
│   │ 
│   ├──tile_coordinates_georeference
│   │       A CSV file listing the latitude and longitude of the top-left corner of each image chip raster, used for converting x, y pixel coordinates into geographical coordinates.
│   │ 
│   ├──tile_fishnet_grid
│   │       A 100m x 100m fishnet grid and FID created in ArcGIS Pro for extracting a subset of image chips to assess interobserver reliability.
│   │ 
│   └──tiles
│          Non-georeferenced satellite image tiles (n=30), jpeg format. Each measuring 100 x 100 m. Randomly selected from Gonydale to complete observer annotations from 9 volunteers of varied experience. 
│          The number at the end of the file name is the FID taken from the tile fishnet grid. 
│       
├── Output
│   │  Collection of files exported using the python script. 
│   │  
│   └──tile_images
│       This contains two subfolders: 
│           1. tiles_with_raw_observer_labels_not_georeferenced: Tile jpeg images with raw non-georeferenced observer labels (circles, with colour representing unique observer ID). 
│           2. tile_with_observer_nest_labels_georeferenced: Tile jpeg images containing georeferenced observer labels (squares, with colour representing unique observer ID) and nest GPS coordinates (white circle)
│
├── python_script
│       Processes the data and performs analysis to determine detectability of Tristan Albatrosses in satellite imagery. It uses the data from the different folders and generates all output files. 
│
└── README
	Description of github files, acknowledgements, licencing of script and tiles, funding source. 
```

## Results

The analysis generates key outputs such as:

GLM minimum age: Generalised linear model (GLM) results for the influence of minimum age on the detectability of nesting albatrosses. Males and Females analysed separately.
GLM model comparison: Generalised linear models (GLM) testing the effects of incubating parent (sex, minimum age) and nest characteristics (slope and aspect) on detectability of Tristan albatrosses in a 31 cm resolution satellite image (n=52).  
Chi-squared test: Determine whether the proportion of nesting males and females detectable in the satellite image were equal.
Observer performance: Summary of detection metrics (F-score, precision and recall values) for presumed albatrosses annotated by nine observers relative to gold standard and active nests.
Gold standard: Summary of detection metrics (F-score, precision and recall values) for presumed albatrosses annotated by references and gold standard relative to active nests.
Observer clustered data: Hierarchial clustering of raw observer annotations to create the clustered dataset.

## Reusing or Adapting the Script

If you reuse or adapt this script, please cite the associated manuscript:

Marie R. G. Attard, Richard A. Phillips, Steffen Oppel, Ellen Bowler and Peter T. Fretwell (In Review) Feasibility of using very high-resolution satellite imagery to monitor Tristan albatrosses *Diomedea dabbenena* on Gough Island. Endangered Species Journal.

## Acknowledgements

This study is a contribution to the Ecosystems and Wildlife from Space programmes within the British Antarctic Survey’s Polar Science for Planet Earth initiative, funded by the Natural Environment Research Programme. MRGA is funded by Darwin Plus (DPLUS132). We are grateful to the Tristan da Cunha Conservation Department and Island Administrators for granting permission to conduct this research.

We acknowledge the Conservation Data Management Unit at RSPB, particularly Alex Whittle and Antje Steinfurth, for providing digital elevation models and geographic information, as well as RSPB for supplying breeding boundary data for Tristan albatrosses at Gough Island. Special thanks go to the Gough Island field team—Roelf Daling, Vonica Perold, Kim Stevens, Jaimie Cleeland, Kate Lawrence, and Fabrice LeBouard—for their dedication in collecting and sharing the ground count data that informed this study.

We sincerely thank Penny Clarke for her invaluable assistance as a reference annotator, and Cath Attard, Connor Bamford, Marcia Blyth, Hannah Cubaynes, Hana Merchant, Elizabeth Pearmain, Norman Ratcliffe, and Sally Thorpe for their efforts in completing observer annotations. Finally, we thank Maxar technologies for granting permission to publish satellite image tiles and associated annotations derived from their imagery.

## Licence

The code in this repository is licensed under an open-source license. The satellite images and annotations are subject to the Maxar Satellite Imagery License Agreement: https://www.maxar.com/legal/internal-use-license

## Funding

Funding was provided by the Darwin Plus (grant ID: DPR9S2\1032). For more details, visit the Darwin Initiative project website: https://www.darwininitiative.org.uk/project/DPLUS132