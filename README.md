# Introduction to working with satellite imagery and geospatial data for your arts project

Mark IJzerman

_Earth observation data, whether it is from above (by satellites) or below (by sightings), can be challenging to get in to when you're not a scientist in the field. On the one hand there's the scientific lingo, and on the other hand technical jargon and knowledge of the operations. Yes, there IS a lot of data. Yes, getting to/through it IS confusing. In this session I help you get to grips with the different kinds of geospatial data and how you can use it in your project. I have been teaching myself about this field of work for the past year, and am sharing my knowledge._

_In this hour we will:_

_- Look at an overview of where the data comes from. From sightings to earth observation._

_- Look at different places where data is stored, and how to obtain it._

_- How to bring different kinds of data together, and then export it so we can use it in software which is more suitable for more artistic purposes!_

Good to do before: Install QGIS3: [http://www.qgis.com](http://www.qgis.com), an open-source Geographic Information System.

If you want to work with your data in Touchdesigner for visualisation, please install Touchdesigner. [http://touchdesigner.com](http://touchdesigner.com) If you wish to work with another kind of software, that’s also OK!

Github repository of this workshop: [https://github.com/markijzerman/geospatial_in_td](https://github.com/markijzerman/geospatial_in_td)


## Introduction of project

This is a broad research area and I am an artist who just started dabbling in this. wanted to put together something useful for this workshop, but it is no way scientifically valid.

Ecological data is very often quite static- more static than taxi or train commute data, for example ([https://willgeary.github.io/data/](https://willgeary.github.io/data/)). It is thus about showing the impact on the landscape. This can be done by showing satellite imagery, or interpolating between the available measurements. Example of interactive visualisation ([Global Forest Watch](https://www.globalforestwatch.org)).


## Source data

Data is in lots of different places. There’s a division to be made between source data that is based on satellite imagery, and source data that is based on sightings / counting of sightings. Let’s focus on satellite data first.


### Satellite data

[Thousands of satellites orbiting earth](https://www.pixalytics.com/wp-content/uploads/2014/04/Debris_objects_-_mostly_debris_-_in_low_Earth_orbit_LEO_-_view_over_the_equator.jpg), around ~700 for earth observation. We’ve come a long way since we needed to recover camera rolls of satellites with planes, such as was done [during the Corona mission](https://en.wikipedia.org/wiki/Corona_(satellite)). The sensors these satellites carry varies greatly. A lot of the data is sold by big companies, but a lot of publicly funded satellite programs offer “easy” access to data. Such as ESA’ programs. [Overview of their Earth Observation Missions](https://earth.esa.int/web/guest/missions/esa-eo-missions). Especially the [Sentinel programme](https://m.esa.int/Our_Activities/Observing_the_Earth/Copernicus/Overview4) is interesting. All these satellites carry various instruments, monitoring [different spectra at different time intervals and resolutions](https://webapps.itc.utwente.nl/sensor/default.aspx?view=allsensors).

A lot of this data is available through several portals offered by different providers, such as [ESA’s EObrowser](https://apps.sentinel-hub.com/eo-browser/), [USGS Earth Explorer](https://earthexplorer.usgs.gov), [Google Earth Engine](https://earthengine.google.com), [Google Earth Engine Code](https://code.earthengine.google.com), [NASA’s Earthdata](https://search.earthdata.nasa.gov), and more…

Let’s try to use EObrowser to visualize some data. By combining different spectral bands of specific instruments, different aspects of the landscape can be visualized. 

Let’s focus on the Yrseke area and make a GIF-timelapse of the last year with false-color data. You will need a login to do so. (If you would like to do a timelapse in higher resolution, please [see this Github and use the Google Colab file](https://github.com/markijzerman/SentinelImagery_SRTM_to_TD). I can help you set this up.)

Common analysis techniques on Sentinel-2 data [can be found here](https://www.sentinel-hub.com/develop/documentation/eo_products/Sentinel2EOproducts).

A presentation with[ a good overview can be found here](https://olc.worldbank.org/system/files/Satellite%20data%20and%20open%20source%20solutions%20for%20sustainable%20development%20by%20Rolf%20de%20By.pdf).

There’s also ways to go deeper, to do [more thorough vegetation analysis](https://eos.com/blog/6-spectral-indexes-on-top-of-ndvi-to-make-your-vegetation-analysis-complete/).

Look at different output from different satellites. Sentinel 3, Sentinel 5, etc. The question mark behind each satellite is good to find out about the sensors of that specific satellite.

How healthy is the Oosterschelde? Let’s look at Chlorophyll. [What is chlorophyll?](https://earthobservatory.nasa.gov/global-maps/MY1DMM_CHLORA)

Look at Chlorophyl in the Sentinel-3 data. It is quite low-resolution.

Look at Chlorophyl analysis in Google Earth Engine Code. It has stripes, because of the LANDSAT7[ scan line corrector that failed](https://www.researchgate.net/figure/The-Scan-Line-Corrector-of-Landsat-7-failure-resulting-in-strips-of-data-gaps-in-all_fig6_324537528). This paper [writes about it as well](https://meetingorganizer.copernicus.org/EGU2017/EGU2017-18950.pdf).

Back to EObrowser. Download a High-res tile from EObrowser.

Open [Qgis](http://www.qgis.com) (Open source Geographic Information System), and add XYZ Tiles, New Connection, and add the following URL (_https://a.tile.openstreetmap.org/${z}/${x}/${y}.png_) to add OpenStreetMaps as a base map. Now we have a base map. Zoom in to Yrseke.

Now drop in the image we downloaded from EObrowser. It should appear in the right place on the map. Using software that can georeference data, we can start collecting different kinds of data for our project.


### Processed data

Processing satellite data is a difficult task, and in most cases better left to scientists. There is plenty of data available on a plethora of subjects. Everything from data on biodiversity ([gbif](https://www.gbif.org)), marine life ([EMODnet](http://www.emodnet-biology.eu)), et cetera.

Our government also offers a lot of open data, mainly through [http://data.overheid.nl](http://data.overheid.nl). Different regions have their own portal, [such as Zeeland](https://dataportaal.zeeland.nl), [or Amsterdam](https://data.amsterdam.nl) (although Amsterdam geodata [tends to be hosted here](https://maps.amsterdam.nl/open_geodata/)).

Load some geoJSON, SHP, or other data into Qgis to try it out.

Make sure to check out the Attribute table (right click on the asset), to see more about the data that is included. Classify the data using Symbology (right click the asset, Properties, Symbology, select Categorized from drop-down list, choose a Column, and click “Classify”!). See [Qgis tutorial](https://docs.qgis.org/2.8/en/docs/training_manual/vector_classification/classification.html).

This way you can start exploring the data that is available.

You might encounter data that has to be imported using WMS, WCS or WFS. These are web services that offer data in different ways. WMS offers maps (raster data), while WFS typically offers feature/vector-like data. [Read more here](https://gis.stackexchange.com/questions/80948/what-are-the-differences-between-wms-wfs-wcs-wps).


### Example: creating a map in Touchdesigner

Let’s go back to Yrseke.

To download updating satellite imagery within Qgis, install the Sentinel plugin from the Plug-in menu. Make sure you have a Sentinel Hub account. Log in to the [Sentinel Config](https://apps.sentinel-hub.com/dashboard/#/configurations) and get your API code there. If you copy it into the plug-in and create a new raster layer from within the plug-in, the data should start downloading. You can find the plug in by it’s icon which should be somewhere in Qgis’ taskbar now.

Let’s find some data to use in this area, for example the [“mileubeschermingsgebieden” as found on Dataportaal Zeeland](https://dataportaal.zeeland.nl/dataportaal/srv/dut/catalog.search#/metadata/ffb99293-612c-47fa-a2be-bedd4dea32e1)- areas that are appointed as special to keep the ecology in check. It’s available for download as a Shapefile, so let’s choose that format.

Other handy sources for data about this area:

[Zeeuws Bodemvenster](https://www.zeeuwsbodemvenster.nl/themas/water/voorkomen-zoet-en-zout-grondwater) has info on if water is salt, sweet etc.

[https://www.zeeuwsbodemvenster.nl/themas/water/voorkomen-zoet-en-zout-grondwater](https://www.zeeuwsbodemvenster.nl/themas/water/voorkomen-zoet-en-zout-grondwater)

Rijkswaterstaat has [good measurements up for download: on the salinity of the water, for example](https://waterinfo.rws.nl/#!/kaart/zouten/).

Also try different sources on Dataportaal Zeeland.

Even though the Netherlands is flat, we might want a height map for our project. Let’s download the “SRTM Downloader” from the Qgis plugins. Click on the icon in the taskbar. You will need a NASA Earthdata account. SRTM stands for “Shuttle Radar Topography Mission”, and carries data that is converted into a DEM: Digital Elevation Model.

Now we have a false-color map of the area, some shapefiles outlining features on the map, maybe some points with data in them, all georeferenced.

The problem is that as opposed to Qgis, the software we are going to use (Touchdesigner, Max, etc.) does not know about positions on Earth. So we need to keep everything within a specific frame. To do that, we can export our data as high-res images, all separately. Let’s first make a Print Layout. In Qgis, go to Project > New Print Layout. On the left, find the button that says “Adds a new Map to the Layout”, and drag it over the full extent of the print layout page. It will render for a while and now display your map. From here you can export your map- choose “Export as Image” and make sure it’s a high resolution (300DPI or so). Make sure to do this for all of your layers separately- so make sure only one layer is visible at a time. This way you end up with heightmap.png, falsecolor.png and regions.png.

You are now able to load these in to the provided Touchdesigner file, or use them in another program. The heightmap can be used to displace the terrain, the regions can be traced and extruded, and the false color map can be the colormap of your area. The size of the grid in the geo1 object should match the proportions of the saved image files.


### Example: working with time-based measurement data

For this example we will work with salt measurements, [which can be downloaded here in CSV format](https://waterinfo.rws.nl/#!/kaart/zouten/). It takes some time before the download is ready. In the GitHub repository there are example measurments. Look at the different tables. It could be visualized over time by reading out the different measurements consecutively. See the example Touchdesigner file.

This could also be placed on a map to give a better idea of where it is spatially.


## Other resources

Close Up At A Distance - Laura Kurgan

https://forum.step.esa.int/t/how-to-calculate-chlorophyll-a-concentration-from-sentinel-2-images/9837

https://forum.step.esa.int/t/retriving-chlorophyll-and-turbidity-from-sentinel-data/9398

https://www.nemokennislink.nl/publicaties/satelliet-helpt-mosseltelers/

geoservices.rijkswaterstaat.nl

data of europe's marine life http://www.emodnet-biology.eu

https://dataportaal.zeeland.nl

Example of visualisation https://www.youtube.com/watch?v=5t_n3vvI95E