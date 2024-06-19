# Tristan-albatross

The Tristan Albatross Diomedea dabbenena is a critically endangered species that breeds almost exclusively on Gough Island (Tristan da Cunha). Incidental mortality (bycatch) in fisheries and chick predation by invasive house mice Mus musculus have led to an ongoing population decline. Regular on-the-ground monitoring of Tristan Albatross populations may be reduced or discontinued in the future due to financial and logistical constraints, and therefore alternative methods would be required for determining long-term population trends. Here, we assessed the viability of using 31 cm resolution WorldView-4 satellite imagery to count Tristan Albatrosses remotely during the breeding season on Gough Island. Counts of birds in satellite images by a wildlife remote-sensing specialist were compared to GPS coordinates of active nests recorded in the field. In total, birds were visible at only 84 (55.3%) of the 152 active nests in the cloud-free regions of the satellite image captured in February 2018. Acquisition of suitable imagery is a major challenge for this species because its upland nesting sites are prone to low-lying orographic cloud, and only one cloud-free image could be obtained over eight seasons. Incomplete detection because of persistent cloud on the island is such that the Tristan Albatross cannot be counted reliably using 31 cm resolution satellite imagery. Differences in nest attributes and bird plumage did not explain variation in detection probability. The addition of more commercial satellites in orbit may increase the chance of obtaining cloud-free imagery across the island in the future, but until then on-the-ground monitoring must continue to obtain accurate population counts and for the UK to meet its commitments to monitor this critically endangered species.

Annotations were visualised and processed in ArcGIS Pro (version 1.3) and all analysis was conducted in R statistical software (version 4.3.2). All data and R scripts are available here, and are separated into 3 folders:

Folder 1: Tristan albatross satellite detectability
This folder contains the R script, data input and table/figure output for assessing detectability of Tristan albatrosses in 31 cm satellite imagery based on reference annotations. The zipped folder contains the following items:
1."Tristan_albatross_age_sex" csv file containing the minimum age and sex of each nesting bird before and after the satellite image was taken.

2."Tristan_albatross_satellite_detectability" csv file listing all nesting birds that were detected in 31 cm orthorectified satellite image. There are 152 nests in satellite image according to nest GPS coordinates.

3."Tristan_albatross_nest_location" contains the slope and aspect of 152 nests in cloud-free regions of satellite image.

4.R script titled "R_markdown_Tristan_albatross_satellite_detectability". This script contains all analysis for determining influential predictors of Tristan Albatross detectability in 31 cm satellite imagery, using csv files in this folder. The figure and table outputs are in the 'R script output' folder.

5.The outputs from the R script are in the 'R script Output' folder.

Folder 2: Interobserver reliability
This folder contains the R script, data input and table/figure output for assessing interobserver reliability among 9 observers in detecting Tristan albatrosses in 31 cm satellite imagery. The zipped folder contains the following items:

1.Folder containing volunteer instructions and 30 tiles (Dimensions: 100 m x 100 m in jpeg format) extracted from 2017/18 satellite image of Gough Island, which were annotated by 9 volunteers. This includes 24 tiles where Tristan albatross nests were present. All tiles were from the Gonydale and Hummocks breeding area.

2."Clustered_2m_observer_data" csv file contains the 2 m clustered dataset based on agreement between observers. The clustered data was created in ArcGIS Pro. Each row contains a separate clustered tag ID (column A), representing a single presumed albatross. The agreement score (column B) states how many unique observers placed a tag within 2 m of each other at this location. The latitude and longitude (columns H and I) coordinates (WGS 1984 UTM Zone 29S) are taken from a random point within the buffer. Columns E and F show the location of the tag based on the number of pixels across (x) and down (y) from the top left cell of the image chip raster.

3."Reference_annotations_data" csv file contains a read me sheet describing each column, and two additional sheets: one contains a list of all active nests that could be detected in satellite imagery based on reference annotations and the second lists all active nests that could not be seen in satellite imagery based on reference annotations. The number of birds counted inside each image chip (tag ID) is listed under the 'region count' column. This dataset was created in ArcGIS Pro.

4."Tile_ID_coordinate_data" csv file lists the latitude and longitude of the top left cell in each image chip raster. This was used to convert the x, y pixel coordinates of each tag into latitude and longitude using the R script.
Raw data folder containing all the raw output (csv format) from the 9 observers using VGG image annotator (VIA). This dataset was used to assess interobserver reliability.

5.The outputs from the R script are in the 'Figures' and 'R script Output' folder.

Folder 3: Gough Island map
This folder contains all the shapefiles needed to create the map of Gough Island in Figure 1 of the manuscript. The Digital Terrain Model is not included due to licence restrictions.

1.Tristan Albatross nest boundaries on Gough Island including Gonydale and the Hummocks, provided by RSPB.

2.Nest GPS coordinates of Tristan Albatrosses in cloud-free region of satellite image provided by RSPB for the 2017/18 breeding season.

3.Reference annotations (point shapefile) of Tristan Albatrosses in cloud-free region of the satellite image.

4.Fishnet grid (100m x 100m) and FID created in ArcGIS Pro to extract a subset of image chips to assess interobserver reliability.

5.Gough Island landscape features, including coastline, ocean, contours (50 m and 200 m intervals) and mountain peaks. This information was extracted from a <10 m resolution Digital Terrain Model.

Funding
Funding was provided by the Darwin Initiative (grant ID: DPR9S2\1032).
