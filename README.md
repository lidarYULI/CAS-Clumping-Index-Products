# CAS-Clumping-Index-Products
The canopy clumping index (CI) measures the spatial distribution pattern of foliage. Foliage is commonly distributed in a non-random manner. It is aggregated at the canopy, branch, and shoot scales. Theoretically, CI is greater than 0. When CI < 1, the foliage exhibits a clumped distribution. A value of CI = 1 indicates a random distribution of foliage. This software, developed in JavaScript based on Google Earth Engine (GEE), is designed to produce global CI products using the MODIS dataset. It is a visualization tool that runs directly on GEE and allows users to download CI data at user-defined scales.

Currently, CI products are available in TIFF format from March 1, 2000, to May 1, 2020, at regional and global scales, with temporal resolutions ranging from daily to monthly and yearly. Publications related to the methods and technologies are listed at the end of this page. The program consists mainly of the following steps:

(1) Filter image datasets by the specified date range to obtain image collections.

(2) Generate multi-band images containing the required data and stack them into an image collection for CI retrieval.

(3) Retrieve daily CI values based on band calculations and exclude low-quality pixels.

(4) Apply the Savitzky–Golay smoothing filter (SG-filter) to the daily CI collection, then composite monthly or yearly CI products based on a quality indicator, and make them available for download.

The descriptions of software usage are as follows: 

The initialized interface includes a date slider at the top of the map, allowing users to quickly view daily CI values.

<img src="https://github.com/CUGLiving/Clumping-Index-Products/blob/main/softwareShots/startedInterface.jpg" width='500px'>

1) Input the start and end dates, then click on a temporal scale. The available product dates will appear.

<img src="https://github.com/CUGLiving/Clumping-Index-Products/blob/main/softwareShots/inputdate.jpg" width='500px'>

2) Select one of the date items to get the product.

<p float="left">
<img src="https://github.com/CUGLiving/Clumping-Index-Products/blob/main/softwareShots/daily.jpg" height='300px' width='200px'/> <img         src="https://github.com/CUGLiving/Clumping-Index-Products/blob/main/softwareShots/monthly.jpg" height='300px' width='200px'/> <img         src="https://github.com/CUGLiving/Clumping-Index-Products/blob/main/softwareShots/yearly.jpg" height='300px' width='200px'/>
</p>

3) Select to get global or regional products.

<img src="https://github.com/CUGLiving/Clumping-Index-Products/blob/main/softwareShots/dailyImg.jpg" width="500px">

4) Click 'View' to add the date-named image to the map.

<img src="https://github.com/CUGLiving/Clumping-Index-Products/blob/main/softwareShots/loadLayer.jpg" width="500px">

5) Click "Download" to show the GEE download panel. Due to GEE constraints, downloading the global extent (60°S–90°N, 180°E–180°W) will automatically divide the product into nine equal-sized image tiles. You can specify the file name and destination folder.

<p float="left">
<img src="https://github.com/CUGLiving/Clumping-Index-Products/blob/main/softwareShots/export.jpg" width="500px"> <img src="https://github.com/CUGLiving/Clumping-Index-Products/blob/main/softwareShots/exportSettings.jpg" width="500px">
</p>
 
6) When select 'draw a rectangle to export or view,' you can draw one or more rectangles and select one of them to view or download data. The regional data can be directly downloaded as a single image.

<img src="https://github.com/CUGLiving/Clumping-Index-Products/blob/main/softwareShots/regionalExport.jpg" width="500px">

All input datasets except the fraction of vegetation coverage (FCOVER) and global land cover data, are provided by the GEE Data Catalog. The land cover image is a single-year product and the FCOVER is the monthly products. We have uploaded the FCOVER up to May 2020, an it will be continuously uploaded as new products become available. The land cover product can be acquired at http://bioval.jrc.ec.europa.eu/products/glc2000/glc2000.php and the FCOVER data at https://land.copernicus.vgt.vito.be/PDF/portal/Application.html#Home.

The products from March 2000 to May 2020 are recommended, as they can be produced based on the matched FCOVER data. Fortunately, products outside this date range are still available for download, as the program is designed to automatically fetch the nearest adjacent FCOVER data.

There are several instructions, as follows:

1）Please enter the dates in the format "2020-01-01".

2）The exported CI band has been scaled by a factor of 1000.

3）After exporting the global image, you will see nine pieces of the tif in your Google Drive.

4) All products include two bands (CI band and Quality band). More information about the products can be found at the end of this page.

5) The default name for the exported folder is "CIFolder," but you can modify it as needed.

6) The GEE link to this program is https://code.earthengine.google.com/?scriptPath=users%2Flrvings%2FGMap%3AClumpingIndex%2FCAS-CI.


References:

[1] Li, Y., and H. Fang (2022). "Real-Time Software for the Efficient Generation of the Clumping Index and Its Application Based on the Google Earth Engine" Remote Sensing 14(15): 3837. https://doi.org/10.3390/rs14153837.

[2] Wei, S., H. Fang, C. B. Schaaf, L. He, and J. M. Chen (2019). "Global 500 m clumping index product derived from MODIS BRDF data (2001–2017)." Remote Sensing of Environment 232: 111296. https://doi.org/10.1016/j.rse.2019.111296.

[3] Wei, S.; Fang, H. Estimation of canopy clumping index from MISR and MODIS sensors using the normalized difference hotspot and darkspot (NDHD) method: The influence of BRDF models and solar zenith angle Remote Sens. Environ. 2016, 187, 476–491. https://doi.org/10.1016/j.rse.2016.10.039
