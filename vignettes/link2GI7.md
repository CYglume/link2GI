---
author: "Chris Reudenbach"
title: "Reproducible projects"
date: "2024-05-06"
editor_options:
  chunk_output_type: console
output:
  html_document: 
    theme: united
    toc: yes
  rmarkdown: default
  pdf_document:
    latex_engine: xelatex
    toc: yes
urlcolor: blue
vignette: >
  %\VignetteIndexEntry{Reproducible projects}
  %\VignetteEncoding{UTF-8}{inputenc}\
  %\VignetteEngine{knitr::knitr}
---



# Reproducible Project Structure

Reproducible projects in R emphasize streamlined project setup and efficient workflows. There are a number of very helpful tools in the R universe, such as [`renv`](https://cran.r-project.org/package=renv), [`usethis`](https://cran.r-project.org/package=usethis), or [`here`](https://cran.r-project.org/package=here), that range from setting up a stable R environment to generating custom project structures to getting the necessary paths in an easy way. In addition, there are a number of project structure packages and templates for creating easy-to-use and transparent project structures. Namely, [`tinProjects`](https://cran.r-project.org/package=tinyProject), [`prodigenr`](https://cran.r-project.org/package=prodigenr) or [`workflowr`](https://cran.r-project.org/package=workflowr) are R packages designed to facilitate reproducible research through automated project structuring and standardization. They all promote organized project directories, emphasize reproducibility by integrating with tools like `Git' and `renv', and reduce manual setup efforts to ensure consistent and error-free project initialization. These packages help build a solid foundation for research and ensure that best practices include using separate scripts for data processing, analysis, and reporting, and combining code with narrative in R Markdown documents from the start. This organized setup improves reproducibility by making it easier to maintain, share, and replicate research. For a more comprehensive overview, have a look at the [ CRAN Task View Reproducible Research](https://CRAN.R-project.org/view=ReproducibleResearch).

## Why initProj then?
In the context of link2GI, which relies heavily on third-party command-line APIs and requires complex and stable folder and file structures, a flexible, lightweight R project setup greatly improves the integration of OS command-line tools into spatial workflows by
 
1. **Streamlining integration: Simplifies the integration of essential command-line tools such as `GDAL' or the sophisticated `Orfeo Toolbox' (OTB) and the growing universe of r(-)spatial packages for advanced geospatial processing.
2. **Improve data exchange**: Organized variable and metadata management ensures accurate and efficient data transfer between different and especially command-line based processes and APIs.
3. **Enhanced Cross-Platform Compatibility: Facilitates cross-platform adaptability, which is critical when using multiple spatial analysis tools, even more so when using different shells.
4. **Performance Optimization: Switching between generic R and command-line tools takes advantage of the speed and efficiency of command-line tools, which is especially beneficial when handling large spatial datasets.

For this reason, the link2GI package includes a lean and lightweight but focused approach that integrates `git', `renv', and a highly flexible folder and package setup process that is simpler than existing approaches, increasing efficiency, accuracy, and performance in geospatial workflows.

### Using the RStudio GUI

![Use the RStudio Template Option](https://raw.githubusercontent.com/r-spatial/link2GI/master/figures/usegui.gif)

### Using the Console

The basic setup of a default project, which initializes Git and renv, is done with the following call. 

```R
root_folder <- tempdir() # Mandatory, variable must be in the R environment.
envrmt <- initProj(root_folder = root_folder, standard_setup = "baseSpatial")

```

It is easy to customize the folder structure. By default you will create 
```R
link2GI::setup_default()$baseSpatial$folders
```
`[1] "docs"         "docs/figures" "tmp"          "data/source"  "data/results" "data/level0"  "data/level1" `

```R

link2GI::setup_default()$baseSpatial$code_subfolders

```

`[1] "src"           "src/functions"`

Use the `folders` argument to create a specific structure or subfolder structure of your project. 

```R
root_folder <- tempdir() # Mandatory, variable must be in the R environment.
envrmt <- initProj(root_folder = root_folder, standard_setup = "baseSpatial",folders = c("data/rawdata/provider1/", "docs/quarto/"))
```
