# README

A data cleaning and linking project that extracts data from the yearly [S.O. developer surveys ](https://survey.stackoverflow.co/) and upgrades it to a linked RDF format, by referencing [Dbpedia](https://www.dbpedia.org/) for countries and programming languages.
- It contains data from 2020 to 2023.
- Developed as a project for my Open Data Management course.  

`Project Notebook.ipynb` is a Jupyter notebook containing all of the python code that extracts, reorganizes, and links the data. 

## What data did I extract?
List the fields and images
,branch,country,ISO3,age_min,age_max,employment,OS,langs


Each survey respondant was categorized as one of:
- Developer
- Non Developer
- Student
Based on their main occupation.

The fields I focused on extracting from each answer are the following.
- #### Country
	- Where the respondant resides
	- As both name and ISO3 code
	- Linked with Dbpedia
- #### Age
	- Expressed as a range.
- #### Employment Status
	One of:
	- FullTime  
	- Idependent  
	- PartTime  
	- Retired  
	- Student  
	- Unemployed
- #### Operating systems
	- A list of the OSes the user claimed to use.
- #### Programming Languages
	- A list of the languages the user claimed to use.

## Overview of the OWL ontology
#### Classes
![]("https://github.com/AloiDavide/Stack-Overflow-surveys-data-linking/blob/main/ontology_screens/classes.PNG")
#### Data properties
![](https://github.com/AloiDavide/Stack-Overflow-surveys-data-linking/blob/main/ontology_screens/datatype_properties.PNG)
#### Object properties
![](https://github.com/AloiDavide/Stack-Overflow-surveys-data-linking/blob/main/ontology_screens/object_properties.PNG)


## Data cleaning
In a vacuum, the data was very "clean" already, however, the format of both questions and answers was not consistent from year to year, thus I had to standardize it before converting the data to RDF.

Here are some of the **main discrepancies**.
- The age field sometimes gets inserted by the user as a floating point number, while other times it is selected from predetermined ranges.
- Some surveys make a distinction between operating systems used personally or professionally, while others do not.
- Answers with the same meaning are usually worded differently in different surveys.
- The list of languages and operating systems to choose from changes every year, and only some years let the user pick more than one.

### Before and after
to be added


## Visualizations and results
to be added

## Libraries used
- pandas
- numpy
- re (regular expressions)
- country_converter
- urllib.parse
- ast
- SPARQLWrapper
- rdflib
- plotly.express

## Data sources and licenses
- [Stack Overflow annual developer surveys](https://survey.stackoverflow.co/)
	- Released under [ODbL](https://opendatacommons.org/licenses/odbl/1-0/) license.  
- Dataset of [all programming languages](https://www.back4app.com/database/paul-datasets/list-of-all-programming-languages) and their Wikipedia pages.
	- Crucial for linking the languages to dbpedia.
	- License
- [Gapminder](https://www.gapminder.org/data/)
	- Used for population data.
	- Accessed through plotly.express.

All the data in this repository is also available to share, modify and adapt under an [ODbL](https://opendatacommons.org/licenses/odbl/1-0/) license.