# kml_To_shp
Convert KML file to ESRI Shapefile
# KML to SHP

This Python code performs a batch conversion of KML files to ESRI Shapefiles using the ogr2ogr command-line tool.

## Description
.kml and .shp are two commonly used file formats in the geographic information system (GIS) industry for storing and sharing spatial data.

KML stands for Keyhole Markup Language and is an XML-based format used to display geographic data in Google Earth and other mapping applications. KML files can contain multiple layers of data, including points, lines, polygons, images, and 3D models. KML files are commonly used to share geographic information on the web and can be easily viewed using various software applications such as Google Earth and ArcGIS Earth.

ESRI Shapefile (.shp) is a popular geospatial vector data format developed by Esri. It is widely used in GIS applications for storing, analyzing, and sharing geospatial data. A Shapefile consists of several files with different extensions, including .shp, .shx, and .dbf. The .shp file contains the geometry (points, lines, or polygons) of the features, the .shx file contains the index of the feature geometry, and the .dbf file contains the attribute data associated with the features. The Shapefile format is supported by many GIS software packages, including Esri's ArcGIS software and the open-source QGIS software. data.

This code is written in Python and uses the `ogr2ogr` command-line tool to read all .kml files from a folder and then it converts the .kml files into .shp file into separate folder with same name as .kml had.
## Prerequisites
Before using the `ogr2ogr` tool for converting geospatial data between different formats, you need to have the `GDAL` (Geospatial Data Abstraction Library) library installed on your system. `ogr2ogr` is a command-line utility that is part of the GDAL library, and it can handle many different vector and raster data formats.

To install `GDAL`, you can follow these steps:

1. Check if GDAL is already installed on your system by opening a terminal/command prompt and typing `ogr2ogr`. If you see a list of options and usage instructions, GDAL is already installed.

2. If `GDAL` is not installed, you can download and install it using a package manager appropriate for your operating system. For example, on Linux systems, you can install GDAL using the package manager for your Linux distribution. On Windows, you can download the GDAL binary installer from the [OSGeo4W](https://trac.osgeo.org/osgeo4w/) website  or from the [GDAL](https://gdal.org/download.html) website .

3. After installing `GDAL`, make sure to add the `GDAL` binaries to your system's PATH environment variable, so that you can run `ogr2ogr` from any directory in your terminal/command prompt.

Once you have installed `GDAL`, you can use `ogr2ogr` to convert geospatial data between various formats.

Here is a step-by-step breakdown of the code:

## KML to SHP
Here is the code for converting .kml to .shp in bulk mode
```bash
import os
import subprocess
```
Import the `os` and `subprocess` modules which will be used in the script for managing files and running system commands respectively.
```bash
kml_dir = "C:/Users/user/Desktop/Kml_file"
```
Set the variable kml_dir to the path of the directory containing the KML files. This is where the KML files are located.
```bash
shp_dir = "C:/Users/user/Desktop/Kml_file"
```
Set the variable shp_dir to the path of the directory where the Shapefiles will be saved
```bash
for kml_file in os.listdir(kml_dir):
```
Start a `for`loop to iterate through all files in the `kml_dir` directory using the `os.listdir()` function.

```bash
    if kml_file.endswith(".kml"):
```
The if statement checks if the file name ends with `.kml` using the string method `endswith()`. If the condition is true, then the code block following it will execute.
```bash
       shp_file = kml_file.replace(".kml", ".shp")
```
Generate the output Shapefile name by replacing `.kml` extension with `.shp` extension using the `.replace()` method

```bash
       subprocess.call(["ogr2ogr", "-f", "ESRI Shapefile", os.path.join(shp_dir, shp_file), os.path.join(kml_dir, kml_file)])
```
Use the `subprocess.call()` function to run the `ogr2ogr` command-line utility which is used to convert the KML file to a Shapefile. The arguments of the command are passed as a list. The first argument `-f` specifies the output format. In this case, it is ESRI Shapefile. The second argument is the path to the output Shapefile. The third argument is the path to the input KML file.

The `.join()` method is used to combine the directory path and file name into a full file path. The resulting path is passed as an argument to the `subprocess.call()` function.

The for loop continues to the next file in the directory until all files have been processed.

Here is the full code for your better understanding:
```bash
import os
import subprocess

# Path to the directory containing KML files
kml_dir = "C:/Users/user/Desktop/Kml_file"

# Path to the directory where the shapefiles will be saved
shp_dir = "C:/Users/user/Desktop/Kml_file"

# Loop through all KML files in the directory
for kml_file in os.listdir(kml_dir):
    if kml_file.endswith(".kml"):
        # Generate the output shapefile name
        shp_file = kml_file.replace(".kml", ".shp")
        # Use ogr2ogr command to convert KML to shapefile
        subprocess.call(["ogr2ogr", "-f", "ESRI Shapefile", os.path.join(shp_dir, shp_file), os.path.join(kml_dir, kml_file)])
```
## Usage

There are several advantages to using Python to convert KML to SHP in bulk mode. Some of the advantages include:

1. **Efficiency**: Bulk conversion of KML to SHP using Python is a fast and efficient process. This is because Python is a powerful programming language that can handle large datasets with ease.

2. **Automation**: Python allows for the automation of repetitive tasks, which means that once the code is written, it can be executed many times without manual intervention.

3. **Flexibility**: Python provides a wide range of tools and libraries that can be used to manipulate geospatial data. This means that the conversion process can be customized to meet specific project requirements.

4. **Consistency**: Bulk conversion of KML to SHP using Python ensures consistency in the output files. This is because the same code is used to convert all the files, which means that the output will have the same format and structure.

5. **Ease of use**: Python is an easy-to-learn language that is widely used in the geospatial industry. This means that there are many resources available online to help users learn and use Python for geospatial data processing.

6. **Cost-effective**: Python is a free and open-source programming language. This means that there are no licensing costs associated with using Python for geospatial data processing.

Overall, using Python for bulk conversion of KML to SHP provides an efficient, automated, flexible, consistent, and cost-effective solution for processing large volumes of geospatial data.
## Contact ME
* Email: koushikghosh1a2s@gmail.com.

* LinkedIn: [Koushik Ghosh](https://www.linkedin.com/in/koushik-ghosh-490761192/)

* ResearchGate: [Koushik Ghosh](https://www.researchgate.net/profile/Koushik-Ghosh-23)


