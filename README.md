# Introduction
Github repository for data and code used in the manuscript "Access to Surgery in Ecuador using the Enhanced 2-step Floating Catchment Area Approach". Included is 3 main files, outlined in detail below.

Additional publicly available data is required for the E2SFCA process. This includes a population raster, drivetime polygons, and a country shapefile. These are linked below.
- Population raster: Gridded Population of the World Version 4. Available from: http://dx.doi.org/10.7927/H49C6VHW
- Drivetime polygon: Using hereR, which relies on HERE API. Drivetime polygons must be calculated from hospital coordinates. Additional details on using hereR is found in the manuscript. Package details available from https://munterfi.r-universe.dev/hereR.
- Country shapefile: geoBoundaries. Available from https://www.geoboundaries.org/countryDownloads.html.

Once the manuscript has been published, a link to the publication will be provided in the README. Any use of this code should be cited. The supply data and E2SFCA output data is included for data transparency and should not be used without express consent of the authors.

# E2SFCA Code
Code to generate geospatial data using the Enhanced Two-step Floating Catchment Area (E2SFCA) method

This repository contains R code that can be used to generate E2SFCA estimates. This code was used to generate estimates of access to surgical care in Ecuador for national planning purposes and for a publication in process. Naming conventions in code are aligned with the healthcare sector, but this code can function for any geospatial analysis using E2SFCA. The code contains the function calculate_e2sfca, which requires a supply dataset (csv file with hospital identifiers and at least 1 supply value such as number of providers), a drivetime dataset (shapefile with hospital identifiers, drivetime distances in seconds, and drivetime polygons), a raster dataset (tif raster file of population counts at the 1kmx1km scale), and a country shapefile (shapefile defining the boundary of the country). Additional arguments are required, such as the supply variables you want to calculate access for, the coordinate system to use for analysis, the value to set for the gaussian decay function, and other naming/filepath related arguments.

# "Supply" Dataset
Included is the hospital supply data used for this publication. In order to use supply data with the above code, it must follow a specific structure. There should be one hospital per row, with columns including a hospital identifier, the coordinates of the hospital, and any number of supply variables as an integer. In this case, the supply variables are the number of SAO providers and the number of surgical procedures. In order to ensure privacy for individual hospitals and individual providers, we follow HCUP guidelines in making this data available to the public. This includes removal of coordinates (which could geolocate facilities specifically) and censoring supply fields that are less than or equal to 10. There are plans for publication of the full, unrestricted dataset with public publication of the national surgical plan of Ecuador. When this is done, the dataset will be updated.

# Output Dataset
Include is the output of the E2SFCA process. The dataset includes over 250000 datapoints representing the geospatial access to surgery in Ecuador. The variables "SPAI.Rj.Sj.WorkforceSAO" and	"SPAI.Rj.Sj.VolumeSurgical" represent the access, as "Spatial Access Index" or "SPAI", to the supply variables used in this study.
