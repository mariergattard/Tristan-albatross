# Tristan Albatross Satellite Detection Analysis
This Python script analyses the detectability of Tristan Albatrosses (Diomedea dabbenena) in high-resolution WorldView-4 satellite imagery (31 cm resolution) captured over Gough Island, Tristan da Cunha. The goal is to assess the feasibility of remotely counting the population of this critically endangered species during the breeding season.

Table of Contents
Introduction
Data
Script Overview
Installation
Usage
Output
Reusing or Adapting the Script
Licence
Funding
Introduction
The Tristan Albatross is a critically endangered species, with a declining population due to bycatch and predation. Monitoring efforts face challenges due to financial constraints, and satellite imagery offers a potential alternative for population monitoring. This analysis uses WorldView-4 satellite imagery to determine how visible albatrosses are in the satellite data.

The Python script provided helps automate this analysis, processing satellite imagery data and generating the required figures and tables to evaluate the detection of Tristan Albatrosses.

Data
All data for this project is organised into subfolders within the Data folder as described below:

Nest Boundaries: Shapefiles of Tristan Albatross nest boundaries on Gough Island, including Gonydale and the Hummocks, provided by RSPB.
GPS Coordinates: GPS coordinates of Tristan Albatross nests in cloud-free regions of the satellite image, provided by RSPB for the 2017/18 breeding season.
Reference Annotations: Point shapefiles of Tristan Albatrosses in cloud-free regions of the satellite image.
Fishnet Grid and FID: A 100m x 100m fishnet grid and FID created in ArcGIS Pro for extracting a subset of image chips to assess interobserver reliability.
Gough Island Landscape Features: Shapefiles for Gough Island’s landscape features (coastline, ocean, contours, and mountain peaks), extracted from a Digital Terrain Model with <10 m resolution.
Bird Information:
Tristan_albatross_age_sex.csv: Minimum age and sex of each nesting bird.
Tristan_albatross_satellite_detectability.csv: Listing of nesting birds detected in the 31 cm orthorectified satellite image (152 nests).
Tristan_albatross_nest_location.csv: Slope and aspect data of 152 nests.
Reference Annotations Data: A CSV file with a readme sheet, listing all active nests detected in satellite imagery and those that could not be detected. The 'region count' column lists the number of birds counted within each image chip.
Tile ID Coordinates: A CSV file listing the latitude and longitude of the top-left corner of each image chip raster, used for converting x,y pixel coordinates into geographical coordinates.
Raw Data Folder: Contains CSV files with raw output from 9 observers using VGG Image Annotator (VIA), which is used for assessing interobserver reliability.
Script Overview
The Python script processes the data and performs the necessary analysis to determine the visibility and detectability of Tristan Albatrosses in satellite imagery. It uses the input data from the various folders and generates output plots and tables for further analysis.

Script Workflow:
Loads the necessary data (CSV, XLSX, or JPEG files from the Data folder).
Processes the satellite imagery data and field survey nest GPS coordinates.
Conducts an analysis to assess albatross detectability based on various predictors.
Generates output plots (figures) and tables, which are saved in the output folder.
Installation
To run this analysis, you'll need Python installed along with the required dependencies. Here's how to get started:

Clone the repository:

bash
Copy code
git clone https://github.com/your-username/project-name.git
cd project-name
Set up a virtual environment (recommended):

bash
Copy code
python -m venv venv
Install the required dependencies:

bash
Copy code
pip install -r requirements.txt
If no requirements.txt is available, manually install the necessary Python packages (e.g., pandas, matplotlib, numpy, etc.).

Usage
This script was originally written in Jupyter Notebook. To run it, follow the steps below:

Install Jupyter Notebook if it's not already installed:

bash
Copy code
pip install jupyterlab
Run the script in Jupyter Notebook:

Open the Jupyter Notebook interface:

bash
Copy code
jupyter notebook
In the Jupyter interface, navigate to the folder where your script is located and open the Python script (tristan_albatross_analysis.ipynb). Then, run the notebook cells one by one.

Make sure the input data is in the correct location:

The Data folder should be placed in the same directory as the notebook and should contain all the required data files.
The output folder will store the results of the analysis (figures and tables).
Run the notebook by selecting each cell and clicking "Run" or use Shift + Enter to execute the cells.

Example Input/Output
Input: Satellite image data, nest coordinates, and volunteer-labelled data.
Output: Generated figures (plots) and tables stored in the output folder.
Output
The script generates the following outputs:

Figures: Graphs and visualisations showing albatross detectability and observer reliability.
Tables: Quantitative data related to the analysis of detectability, observer agreement, and other factors.
All output will be saved in the output folder.

Reusing or Adapting the Script
Please cite our manuscript if you reuse or adapt this script:

Marie R. G. Attard, Richard A. Phillips, Steffen Oppel, Ellen Bowler and Peter T. Fretwell (In Review) Feasibility of using very high-resolution satellite imagery to monitor Tristan albatrosses Diomedea dabbenena on Gough Island. Endangered Species Journal.

Licence
The satellite images used in this study are under the Maxar Satellite Imagery licence agreement: https://www.maxar.com/legal/internal-use-license

Funding
Funding was provided by the Darwin Plus (grant ID: DPR9S2\1032). Further project information can be found on the Darwin Initiative website:  https://www.darwininitiative.org.uk/project/DPLUS132
