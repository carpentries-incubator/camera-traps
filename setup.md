---
layout: page
title: Setup
---

# Overview

This workshop is designed to be run on your local machine. First, you will need to download the data we use in the workshop. Then, you need to set up your machine to analyze and process geospatial data. We provide instructions below to install all components manually.

## Data

You can download all of the data used in this workshop by clicking
[this download link](https://figshare.com/s/5842d402413069e51daf). The file is ~100 MB.

Clicking the download link will automatically download all of the files to your default download directory as a single compressed
(`.zip`) file. To expand this file, double click the folder icon in your file navigator application (for Macs, this is the Finder
application).

For a full description of the data used in this workshop see the [data page](data).

## Option A: Local Installation

### Software

| Software | Install | Manual | Available for | Description |
| -------- | ------------ | ------ | ------------- | ----------- |
| [GDAL](http://www.gdal.org) | [Link](https://gdal.org/download.html) | [Link](https://gdal.org) | Linux, MacOS, Windows | Geospatial model for reading and writing a variety of formats |
| [GEOS](https://trac.osgeo.org/geos) | [Link](https://trac.osgeo.org/geos) | [Link](http://geos.osgeo.org/doxygen/) | Linux, MacOS, Windows | Geometry models and operations |
| [PROJ.4](http://proj4.org) | [Link](http://proj4.org/install.html)| [Link](http://proj4.org/index.html)| Linux, MacOS, Windows | Coordinate reference system transformations |
| [R](https://www.r-project.org) | [Link](https://cloud.r-project.org) | [Link](https://cloud.r-project.org) | Linux, MacOS, Windows | Software environment for statistical and scientific computing |
| [RStudio](https://www.rstudio.com) | [Link](https://www.rstudio.com/products/rstudio/download/#download) | | Linux, MacOS, Windows | GUI for R |
| [UDUNITS](https://www.unidata.ucar.edu/software/udunits/) | [Link](https://www.unidata.ucar.edu/downloads/udunits/index.jsp) | [Link](https://www.unidata.ucar.edu/software/udunits/#documentation) | Linux, MacOS, Windows | Unit conversions |

We provide quick instructions below for installing the various software needed for this workshop. At points, they assume familiarity with the command line and with installation in general. As there are different operating systems and many different versions of operating systems and environments, these may not work on your computer. If an installation doesn't work for you, please refer to the installation instructions for that software listed in the table above.


### GDAL, GEOS, and PROJ.4

The installation of the geospatial libraries GDAL, GEOS, and PROJ.4 varies significantly based on operating system. These are all dependencies for `sf`, the `R` package that we will be using for spatial data operations throughout this workshop.

> ## Windows
>
>To install the geospatial libraries, install the latest version [RTools](https://cran.r-project.org/bin/windows/Rtools/)
>
{: .solution}

> ## macOS - Install with Packages (Beginner)
>
> The simplest way to install these geospatial libraries is to install the latest version of [Kyng Chaos's pre-built package](http://www.kyngchaos.com/software/frameworks) for GDAL Complete. Be aware that several other libraries are also installed, including the UnixImageIO, SQLite3, and `NumPy`.
>
> After downloading the package in the link above, you will need to double-click the cardbord box icon to complete the installation. Depending on your security settings, you may get an error message about "unidentified developers". You can enable the installation by following [these instructions](https://kb.wisc.edu/page.php?id=25443) for installing programs from unidentified developers.
>
{: .solution}

> ## macOS - Install with Homebrew (Advanced)
>
> Alternatively, participants who are comfortable with the command line can install the geospatial libraries individually using [homebrew](https://brew.sh):
>
>~~~
>$ brew tap osgeo/osgeo4mac && brew tap --repair
>$ brew install proj
>$ brew install geos
>$ brew install gdal2
>~~~
>{: .language-bash}
>
{: .solution}

> ## Linux
>
> Steps for installing the geospatial libraries will vary based on which form of Linux you are using. These instructions are adapted from the [`sf` package's `README`](https://github.com/r-spatial/sf).
>
> For **Ubuntu**:
>
>~~~
>$ sudo add-apt-repository ppa:ubuntugis
>$ sudo apt-get update
>$ sudo apt-get install libgdal-dev libgeos-dev libproj-dev
>~~~
>{: .language-bash}
>
> For **Fedora**:
>
>~~~
>$ sudo dnf install gdal-devel proj-devel proj-epsg proj-nad geos-devel
>~~~
>{: .language-bash}
>
> For **Arch**:
>
>~~~
>$ pacman -S gdal proj geos
>~~~
>{: .language-bash}
>
> For **Debian**: The [rocker geospatial](https://github.com/rocker-org/geospatial) Dockerfiles may be helpful. Ubuntu Dockerfiles are found [here](https://github.com/r-spatial/sf/tree/master/inst/docker). These may be helpful to get an idea of the commands needed to install the necessary dependencies.
>
{: .solution}

### UDUNITS

Linux users will have to install UDUNITS separately. Like the geospatial libraries discussed above, this is a dependency for the `R` package `sf`. Due to conflicts, it does not install properly on Linux machines when installed as part of the `sf` installation process. It is therefore necessary to install it using the command line ahead of time.

> ## Linux
>
> Steps for installing the geospatial will vary based on which form of Linux you are using. These instructions are adapted from the [`sf` package's `README`](https://github.com/r-spatial/sf).
>
> For **Ubuntu**:
>
>~~~
>$ sudo apt-get install libudunits2-dev
>~~~
>{: .language-bash}
>
> For **Fedora**:
>
>~~~
>$ sudo dnf install udunits2-devel
>~~~
>{: .language-bash}
>
> For **Arch**:
>
>~~~
>$ pacaur/yaourt/whatever -S udunits
>~~~
>{: .language-bash}
>
> For **Debian**:
>
>~~~
>$ sudo apt-get install -y libudunits2-dev
>~~~
>{: .language-bash}
>
{: .solution}


### R

Participants who do not already have `R` installed should download and install it.

> ## Windows
>
>To install `R`, Windows users should select "Download R for Windows" from RStudio and CRAN's [cloud download page](https://cloud.r-project.org), which will automatically detect a CRAN mirror for you to use. Select the `base` subdirectory after choosing the Windows download page. A `.exe` executable file containing the necessary components of base R can be downloaded by clicking on "Download R 3.x.x for Windows".
>
{: .solution}

> ## macOS
>
>To install `R`, macOS users should select "Download R for (Mac) OS X" from RStudio and CRAN's [cloud download page](https://cloud.r-project.org), which will automatically detect a CRAN mirror for you to use. A `.pkg` file containing the necessary components of base R can be downloaded by clicking on the first available link (this will be the most recent), which will read `R-3.x.x.pkg`.
>
{: .solution}

> ## Linux
>
>To install `R`, Linux users should select "Download R for Linux" from RStudio and CRAN's [cloud download page](https://cloud.r-project.org), which will automatically detect a CRAN mirror for you to use. Instructions for a number of different Linux operating systems are available.
>
{: .solution}

### RStudio
RStudio is a GUI for using `R` that is available for Windows, macOS, and various Linux operating systems. It can be downloaded [here](https://www.rstudio.com/products/rstudio/download/). You will need the **free** Desktop version for your computer. *In order to address issues with `ggplot2`, learners and instructors should run a recent version of RStudio (v1.2 or greater).*

### R Packages

The following `R` packages are used in the various geospatial lessons.

* [`dplyr`](https://cran.r-project.org/package=dplyr)
* [`raster`](https://cran.r-project.org/package=raster)
* [`rgdal`](https://cran.r-project.org/package=rgdal)
* [`sf`](https://cran.r-project.org/package=sf)
* [`camtrapR`](https://cran.r-project.org/package=camtrapR)
* [`stringr`](https://cran.r-project.org/package=stringr)


To install these packages in RStudio, do the following:  
1\. Open RStudio by double-clicking the RStudio application icon. You should see
something like this:

![RStudio layout](/fig/01-rstudio.png)


2\. Type the following into the console and hit enter.

~~~
install.packages(c("dplyr", "raster", "rgdal", "sf", "camtrapR", "stringr"))
~~~
{: .language-r}

You should see a status message starting with:

~~~
trying URL 'https://cran.rstudio.com/bin/macosx/el-capitan/contrib/3.5/dplyr_0.7.6.tgz'
Content type 'application/x-gzip' length 5686536 bytes (5.4 MB)
==================================================
downloaded 5.4 MB
~~~
{: .output}

When the installation is complete, you will see a status message like:

~~~
The downloaded binary packages are in
/var/folders/7g/r8_n81y534z0vy5hxc6dx1t00000gn/T//RtmpJECKXM/downloaded_packages
~~~
{: .output}

You are now ready for the workshop!

>{: .language-bash}
>
{: .solution}
