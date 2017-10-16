---
layout: single
title: "Calculate and plot difference normalized burn ratio (dNBR) from Landsat remote sensing data in R"
excerpt: "In this lesson we review how to calculate difference normalized burn ratio using pre and post fire NBR rasters in R. We finally will classify the dNBR raster."
authors: ['Leah Wasser','Megan Cattau']
<<<<<<< HEAD
modified: '2017-10-16'
=======
modified: '2017-10-11'
>>>>>>> 6372458388f8a575c7eda33957800a42f30d34cb
category: [courses]
class-lesson: ['multispectral-normalized-burn-ratio']
permalink: /courses/earth-analytics/spectral-remote-sensing-modis/calculate-dNBR-R-Landsat/
nav-title: 'dNBR with Landsat'
module-title: 'Normalized Burn Ration'
module-description: '. '
module-nav-title: 'Fire / spectral remote sensing data - in R'
module-type: 'class'
class-order: 3
week: 8
course: "earth-analytics"
sidebar:
  nav:
author_profile: false
comments: true
order: 1
topics:
  remote-sensing: ['landsat', 'modis']
  earth-science: ['fire']
  reproducible-science-and-programming:
  spatial-data-and-gis: ['raster-data']
lang-lib:
  r: []
redirect_from:
   - "/courses/earth-analytics/week-6/calculate-dNBR-R-Landsat/"
   - "/courses/earth-analytics/spectral-remote-sensing-landsat/calculate-dNBR-R-Landsat/"

---


{% include toc title="In This Lesson" icon="file-text" %}

<div class='notice--success' markdown="1">

## <i class="fa fa-graduation-cap" aria-hidden="true"></i> Learning Objectives

After completing this tutorial, you will be able to:

* Calculate `dNBR` in `R`
* Describe how the `dNBR` index is used to quantify fire severity.

## <i class="fa fa-check-square-o fa-2" aria-hidden="true"></i> What you need

You will need a computer with internet access to complete this lesson and the
data for week 6 of the course.

{% include/data_subsets/course_earth_analytics/_data-week6-7.md %}
</div>

As mentioned in the previous lesson, we can use NBR to map the extent and severity of a fire.
Let's explore creating NBR using Landsat data.

## Calculate dNBR using Landsat data

First, let's setup our spatial packages.


<<<<<<< HEAD
```r
# load spatial packages
library(raster)
library(rgdal)
library(rgeos)
library(RColorBrewer)
# turn off factors
options(stringsAsFactors = FALSE)
```
=======
>>>>>>> 6372458388f8a575c7eda33957800a42f30d34cb

Next, we open up our landsat data and create a spatial raster stack.



<<<<<<< HEAD
```r
# create stack
all_landsat_bands_pre <- list.files("data/week_07/Landsat/LC80340322016189-SC20170128091153/crop",
           pattern=glob2rx("*band*.tif$"),
           full.names = TRUE) # use the dollar sign at the end to get all files that END WITH
all_landsat_bands_pre
=======
```
>>>>>>> 6372458388f8a575c7eda33957800a42f30d34cb
## [1] "data/week_07/Landsat/LC80340322016189-SC20170128091153/crop/LC80340322016189LGN00_sr_band1_crop.tif"
## [2] "data/week_07/Landsat/LC80340322016189-SC20170128091153/crop/LC80340322016189LGN00_sr_band2_crop.tif"
## [3] "data/week_07/Landsat/LC80340322016189-SC20170128091153/crop/LC80340322016189LGN00_sr_band3_crop.tif"
## [4] "data/week_07/Landsat/LC80340322016189-SC20170128091153/crop/LC80340322016189LGN00_sr_band4_crop.tif"
## [5] "data/week_07/Landsat/LC80340322016189-SC20170128091153/crop/LC80340322016189LGN00_sr_band5_crop.tif"
## [6] "data/week_07/Landsat/LC80340322016189-SC20170128091153/crop/LC80340322016189LGN00_sr_band6_crop.tif"
## [7] "data/week_07/Landsat/LC80340322016189-SC20170128091153/crop/LC80340322016189LGN00_sr_band7_crop.tif"
<<<<<<< HEAD

# stack the data
landsat_stack_pre <- stack(all_landsat_bands_pre)
=======
>>>>>>> 6372458388f8a575c7eda33957800a42f30d34cb
```

Next we calculate dNBR using the following steps:

1. Open up pre-fire data and calculate *NBR*
2. Open up the post-fire data and calculate *NBR*
3. Calculate **dNBR** (difference NBR) by subtracting post-fire NBR from pre-fire NBR.
4. Classify the dNBR raster using the classification table below.

. Note the code to do this is hidden. You will need to figure
out what bands are required to calculate NBR using Landsat.

<<<<<<< HEAD
<img src="{{ site.url }}/images/rfigs/earth-analytics/00-course-overview/2017-01-01-course-home/calculate-nbr-1.png" title="landsat derived NDVI plot" alt="landsat derived NDVI plot" width="90%" />
=======
<img src="{{ site.url }}/images/rfigs/courses/earth-analytics/week08/2017-02-22-spectral07-calculate-NBR-with-landsat-R/calculate-nbr-1.png" title="landsat derived NDVI plot" alt="landsat derived NDVI plot" width="90%" />
>>>>>>> 6372458388f8a575c7eda33957800a42f30d34cb


You can export the NBR raster if you want using `writeRaster()`.


<<<<<<< HEAD
```r
writeRaster(x = landsat_nbr_pre,
              filename="data/week_07/outputs/landsat_nbr",
              format = "GTiff", # save as a tif
              datatype='INT2S', # save as a INTEGER rather than a float
              overwrite = T)
```
=======
>>>>>>> 6372458388f8a575c7eda33957800a42f30d34cb


Next, we can open the post-fire landsat data to calculate post-fire NBR.


<<<<<<< HEAD
```r
all_landsat_bands_post <- list.files("data/week_07/Landsat/LC80340322016205-SC20170127160728/crop",
           pattern=glob2rx("*band*.tif$"),
           full.names = TRUE) # use the dollar sign at the end to get all files that END WITH
all_landsat_bands_post
=======
```
>>>>>>> 6372458388f8a575c7eda33957800a42f30d34cb
## [1] "data/week_07/Landsat/LC80340322016205-SC20170127160728/crop/LC80340322016205LGN00_sr_band1_crop.tif"
## [2] "data/week_07/Landsat/LC80340322016205-SC20170127160728/crop/LC80340322016205LGN00_sr_band2_crop.tif"
## [3] "data/week_07/Landsat/LC80340322016205-SC20170127160728/crop/LC80340322016205LGN00_sr_band3_crop.tif"
## [4] "data/week_07/Landsat/LC80340322016205-SC20170127160728/crop/LC80340322016205LGN00_sr_band4_crop.tif"
## [5] "data/week_07/Landsat/LC80340322016205-SC20170127160728/crop/LC80340322016205LGN00_sr_band5_crop.tif"
## [6] "data/week_07/Landsat/LC80340322016205-SC20170127160728/crop/LC80340322016205LGN00_sr_band6_crop.tif"
## [7] "data/week_07/Landsat/LC80340322016205-SC20170127160728/crop/LC80340322016205LGN00_sr_band7_crop.tif"
<<<<<<< HEAD

# stack the data
landsat_stack_post <- stack(all_landsat_bands_post)
=======
>>>>>>> 6372458388f8a575c7eda33957800a42f30d34cb
```

Then we calculate NBR on the post data - note the code here is purposefully hidden.
You need to figure out what bands to use to perform the math!

<<<<<<< HEAD
<img src="{{ site.url }}/images/rfigs/earth-analytics/00-course-overview/2017-01-01-course-home/calculate-nbr-post-1.png" title="landsat derived NBR post fire" alt="landsat derived NBR post fire" width="90%" />

Finally, calculate the DIFFERENCE between the pre and post NBR!!


```r
# calculate difference
landsat_nbr_diff <- landsat_nbr_pre - landsat_nbr_post
plot(landsat_nbr_diff,
     main = "Difference NBR map \n Pre minus post Cold Springs fire",
     axes=F, box=F)
```

<img src="{{ site.url }}/images/rfigs/earth-analytics/00-course-overview/2017-01-01-course-home/unnamed-chunk-1-1.png" title="Difference NBR map" alt="Difference NBR map" width="90%" />
=======
<img src="{{ site.url }}/images/rfigs/courses/earth-analytics/week08/2017-02-22-spectral07-calculate-NBR-with-landsat-R/calculate-nbr-post-1.png" title="landsat derived NBR post fire" alt="landsat derived NBR post fire" width="90%" />

Finally, calculate the DIFFERENCE between the pre and post NBR!!

<img src="{{ site.url }}/images/rfigs/courses/earth-analytics/week08/2017-02-22-spectral07-calculate-NBR-with-landsat-R/unnamed-chunk-1-1.png" title="Difference NBR map" alt="Difference NBR map" width="90%" />
>>>>>>> 6372458388f8a575c7eda33957800a42f30d34cb

When you have calculated dNBR or the difference in NBR pre minus post fire,
classify the output raster using the `classify()` function and the classes below.

| SEVERITY LEVEL  | | dNBR RANGE |
|------------------------------|
| Enhanced Regrowth | | > -.1 |
| Unburned       |  | -.1 to +.1 |
| Low Severity     | | +.1 to +.27 |
| Moderate Severity  | | +.27 to +.66 |
| High Severity     |  |  > +1.3 |

NOTE: your min an max values for NBR may be slightly different from the table
shown above! If you have a smaller min value (< -700) then adjust your first class
to that smallest number. If you have a largest max value (>1300) then adjust
your last class to that largest value in your data.

Alternatively, you can use the `Inf` to specify the smallest `-Inf` and largest
`Inf` values.





Your classified map should look something like:

<<<<<<< HEAD
<img src="{{ site.url }}/images/rfigs/earth-analytics/00-course-overview/2017-01-01-course-home/classify-output-plot-1.png" title="classified NBR output" alt="classified NBR output" width="90%" />
=======
<img src="{{ site.url }}/images/rfigs/courses/earth-analytics/week08/2017-02-22-spectral07-calculate-NBR-with-landsat-R/classify-output-plot-1.png" title="classified NBR output" alt="classified NBR output" width="90%" />
>>>>>>> 6372458388f8a575c7eda33957800a42f30d34cb

## Compare to fire boundary

As an example to see how our fire boundary relates to the boundary that we've
identified using MODIS data, we can create a map with both layers. I'm using
the shapefile in the folder:

`data/week_07/vector_layers/fire-boundary-geomac/co_cold_springs_20160711_2200_dd83.shp`

Add fire boundary to map.

<<<<<<< HEAD
<img src="{{ site.url }}/images/rfigs/earth-analytics/00-course-overview/2017-01-01-course-home/classify-output-plot2-1.png" title="classified NBR output" alt="classified NBR output" width="90%" />
=======
<img src="{{ site.url }}/images/rfigs/courses/earth-analytics/week08/2017-02-22-spectral07-calculate-NBR-with-landsat-R/classify-output-plot2-1.png" title="classified NBR output" alt="classified NBR output" width="90%" />
>>>>>>> 6372458388f8a575c7eda33957800a42f30d34cb




Make it look a bit nicer using a colorbrewer palette. I used the
`RdYlGn` palette:

`brewer.pal(5, 'RdYlGn')`


<<<<<<< HEAD
<img src="{{ site.url }}/images/rfigs/earth-analytics/00-course-overview/2017-01-01-course-home/classify-output-plot3-1.png" title="classified NBR output" alt="classified NBR output" width="90%" />
=======
<img src="{{ site.url }}/images/rfigs/courses/earth-analytics/week08/2017-02-22-spectral07-calculate-NBR-with-landsat-R/classify-output-plot3-1.png" title="classified NBR output" alt="classified NBR output" width="90%" />
>>>>>>> 6372458388f8a575c7eda33957800a42f30d34cb

Note that you will have to figure out what date these data are for! I purposefully
didn't include it in the title of this map.




<<<<<<< HEAD

```r
barplot(nbr_classified,
        main = "Distribution of Classified NBR Values",
        col = the_colors)
```

<img src="{{ site.url }}/images/rfigs/earth-analytics/00-course-overview/2017-01-01-course-home/view-bar-1.png" title="plot barplot of fire severity values" alt="plot barplot of fire severity values" width="90%" />

Add labels to your barplot!


```r
barplot(nbr_classified,
        main = "Distribution of Classified NBR Values",
        col = the_colors,
        names.arg = c("Enhanced \nRegrowth", "Unburned", "Low \n Severity", "Moderate \n Severity", "High \nSeverity"))
```

<img src="{{ site.url }}/images/rfigs/earth-analytics/00-course-overview/2017-01-01-course-home/view-barplot1-1.png" title="plot barplot of fire severity values with labels" alt="plot barplot of fire severity values with labels" width="90%" />
=======
<img src="{{ site.url }}/images/rfigs/courses/earth-analytics/week08/2017-02-22-spectral07-calculate-NBR-with-landsat-R/view-bar-1.png" title="plot barplot of fire severity values" alt="plot barplot of fire severity values" width="90%" />

Add labels to your barplot!

<img src="{{ site.url }}/images/rfigs/courses/earth-analytics/week08/2017-02-22-spectral07-calculate-NBR-with-landsat-R/view-barplot1-1.png" title="plot barplot of fire severity values with labels" alt="plot barplot of fire severity values with labels" width="90%" />
>>>>>>> 6372458388f8a575c7eda33957800a42f30d34cb


<div class="notice--warning" markdown="1">

## <i class="fa fa-pencil-square-o" aria-hidden="true"></i> Optional challenge - NBR using MODIS

The table below shows the band ranges for the MODIS sensor. We know that the
NBR index will work with any multispectral sensor with a NIR
band between 760 - 900 nm and a SWIR band between 2080 - 2350 nm.
What bands should we use to calculate NBR using MODIS?

| Band | Wavelength range (nm) | Spatial Resolution (m) | Spectral Width (nm)|
|-------------------------------------|------------------|--------------------|----------------|
| Band 1 - red | 620 - 670 | 250 | 2.0 |
| Band 2 - near infrared | 841 - 876 | 250 | 6.0 |
| Band 3 -  blue/green | 459 - 479 | 500 | 6.0 |
| Band 4 - green | 545 - 565 | 500 | 3.0 |
| Band 5 - near infrared  | 1230 – 1250 | 500 | 8.0  |
| Band 6 - mid-infrared | 1628 – 1652 | 500 | 18 |
| Band 7 - mid-infrared | 2105 - 2155 | 500 | 18 |

</div>


<div class="notice--info" markdown="1">

## Additional Resources

* <a href="http://gsp.humboldt.edu/olm_2015/Courses/GSP_216_Online/lesson5-1/NBR.html" target="_blank">Humboldt GSP Course online NBR lesson</a>

</div>