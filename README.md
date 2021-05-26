
<img src="https://spatial.ucr.edu/images/UCR_logo_long.png" alt="UCR"
	title="University of California" width="300" height="50"  /> 

[![Gitter](https://badges.gitter.im/p280s21project3/community.svg)](https://gitter.im/p280s21project3/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

# PBPL 280 Project: Education and Environmental Justice
## A Comparative Analysis of Exposure to Respiratory Hazards and School Performance in Southern California. ##


## :pushpin: Contributors
[Laura Shah](https://github.com/lsala010/)

[Esteban Villegas](https://github.com/evill092)

[Wajiha Noor](https://github.com/WawNun)

[Preeti Juturu](https://github.com/preetijuturu)

[Salvador Jr. Olguin](https://github.com/Salolg5)

-------

## :hourglass: Project Timeline

----

`May 5, 2021` 

- [x] **Project Proposal Submission**: Project Proposal on HackMD.

`May 19, 2021 `

- [x] **Project Milestone 1**: Paper Outline/ Literature Review & Basic Visualization.

`May 26, 2021 `
- [ ] **Project Milestone 2**: Complete Data Analysis and Visualization.

`June 4, 2021`
- [ ] **Final Submission**: Presentation, Manuscript and Project Reproducibility Documentation. 
 
------

## 📝 Project Documentation
------
- [Project Guidelines](https://sergerey.org/pbpl280s21/projects.html)
 Guidelines from the course instructor.
 
- [Project Folder](https://drive.google.com/drive/u/1/folders/0AOU5SGI5NYK2Uk9PVA)
Google drive for all relevant files shared with the group members.

-  [HackMD for Proposal Writeup](https://hackmd.io/@xSZKUBllSUCUfYxmgoh_yA/SyurmYCUd)
Project proposal for our final project.
  
- [HackMD for Literature Review](https://hackmd.io/@Laura786/S15WsEJ__/edit)
Review of the past literature -A total of 12 papers will reviewed for the study.

- [HackMD for Codebook Data Selection](https://hackmd.io/@Laura786/ryJBHa-uu/edit) 
 Organizing the data, identifying potential variables, and sources. 
 
- [Code in Python ](https://github.com/preetijuturu/p280s21project3/tree/main/Codebook)
 Multiple python notebooks for the data analysis.
 
 - [Project Manuscript](https://github.com/preetijuturu/p280s21project3/blob/main/Manuscript.md)
   Compiling research elements into a manuscript.
 ------
 
##  :clipboard: Data Sources
----
A complete list of the main data sources and code to retrieve data for the study.
 
1. National Center for Education Statistics 
 
   - [NCES](https://open.quiltdata.com/b/spatial-ucr/tree/nces/schools/) 

```
schools = gpd.read_parquet('s3://spatial-ucr/nces/schools/schools_1718.parquet')

```
2. The Educational Opportunity Project at Stanford University 

    - [SEDA](https://edopportunity.org/) 
  
```
SEDA = pd.read_csv("https://stacks.stanford.edu/file/druid:db586ns4974/seda_cov_school_poolyr_4.0.csv")

```
3. United States Environmental Protection Agency(EPA) EJSCREEN

    - [EPA](https://open.quiltdata.com/b/spatial-ucr/tree/epa/ejscreen/)
    - https://cgshub.space/user/lsala010/doc/tree/p280s21project3/Codebook/EJ__V2.ipynb

```
import quilt3
b = quilt3.Bucket("s3://spatial-ucr")
b.fetch("epa/ejscreen/ejscreen_2020.parquet", "./ejscreen_2020.parquet")
ejscreen = pd.read_parquet('ejscreen_2020.parquet')
```

 4. Census Bureau's TIGERLINE FILES
     - [Elementary School Districts]( http://www2.census.gov/geo/tiger/TIGER2010DP1/ELSD_2010Census_DP1.zip)
     - [Census Bureau's TIGER database documentation]( https://www.census.gov/programs-surveys/saipe/technical-documentation/methodology/school-districts/overview-school-district.html)
     - [See the boundary files on this page]( https://www.census.gov/geographies/mapping-files/2010/geo/tiger-data.html)

```
tracts = gpd.read_parquet("s3://spatial-ucr/census/acs/acs_2018_tract.parquet")
```
----

## 🛠️ Additional Resources

Repository- Introduction to Geospatial Data Analysis with Python
https://github.com/sjsrey/gdapy18

----
## 🗃️ Article/Readings
[As 'diesel death zones' spread in California, pollution regulators place new rules on warehouse industry](https://phys.org/news/2021-05-diesel-death-zones-california-pollution.html)



-----
 ## :speech_balloon: Questions
 
 Pending Decisions
 - Which type of school (public, private, charter school)
- Time period for analysis? (crossectional VS longitudinal)
- ALL SCHOOLS (elementary, secondary and highschool) VS ONLY ELEMENTARY schools?
- How do we define school districts? 
- Selection of areas/locations for analysis, for instance Riverside VS Coastal areas?
- One of the things that we were considering was looking at the locations of warehouses to help look at the impact that toxic hazard has on students performance. Would you recommend that we go about that route or would looking at the Environment Justice dataset be enough? 

----

## :dart: Tasks 

Due Date: `05/26/2021`
- Attend group meeting schedule for `05/24/2021`
- Create a combined file containing the clean code.
- Attempt Veroni method on our data.

**Note: Details of each tasks are organized in the projects section of the repo.**

---

## :date: Group Meeting Log
------
`5/24/2021`

- [x]  **Group Meeting with Professor** 
 
 *Agenda: Discuss the issue of multiple legends on the choropleth map and how to create a score combining EJ and School performance.*
 
- Suggestions for the project
* Veroni method:
	* neighborhood (average census block groups) represented by polygons
	* Veroni method entails looking at the locations of schools subdivided within neighborhood polygons 
		* Closest school per polygon 	  
		* Link for visual rep: https://pysal.org/notebooks/lib/libpysal/voronoi.html 
	* Size of polygon depends on the spatial distribution of the points
	* Polygons will have score of schools with EJ Layer 
	* Veroni is another layer that we are adding to our map. 
	* Okay to combine NCES/SEDA/ACS/EJ Data by GeoId. Work from one file.
* Wednesday night Professor will do a demo on how to use the veroni method 
* Policy Perspective of Project: Purposes of project does not require policy recommendation- optional 
	* we can touch on policy implications  
		* Prof: Recommends taxing corporations that emit environmental toxins 	 	 
* Limitations of using Veroni method: 
	* Has constant population density - assumptions 
	* Distance measures as crow flies 
* Date Presentations Due forthcoming 	 
-----

`5/21/2021`
- [x]  **Group Meeting** 

*Agenda: Division of Work*
-  Wajiha and Sal and Esteban looking at SEDA variables and how to interpret 
-  How to access the correlation of the SEDA outcomes and the 
-  Working on the paper and presentation, drafting intro [Preeti will do the intro]
-  Create outline for presentation [Esteban and Laura],
-  Everyone will work on the manuscript; preeti will let us know when there are updates on the manuscript

`Upcoming Task`
- Look into the environmental policy for the inland empire for policy alt.


----
`5/19/2021`
- [x]  **In Class Group Meeting** 

 *Agenda: Discussion on progress made so far and possible questions.*

Laura: 
- create a smaller version of EJ data 
- Then save to local account 
- Use block group to join with EJ 
- Join Everything 
- For analysis: if you are going to look at assocation between demographic and cancer risk; then you should look at Demographics and Cancer risk and not demographics and Cancer Index 
- Look at what Percentile is

Wajiha: 
-  Use School Catchment join 
-  What's the relevant data area around a school? 
-  Think about how you expect the relationship to work between schools and [pollution for example]
-  One possible route for the project is descriptive. 
-  If descriptive then we should use precalculated index (it also depends on our research question)  

Links: 
1. https://github.com/sjsrey/gdapy18
2. https://github.com/sjsrey/gqs18/blob/master/content/geopandas_buffering.org

-----
`5/06/2021`
- [x]  **Group Meeting** 

 *Agenda: Finalized the project proposal in HackMD file.*
 
 ----
 
`4/23/2021` 
 - [x]   **Group Meeting** 

*Agenda: Discussion and review of data and literature for the study.*

 Potential Forms of Measurements
   -  Air Pollution ( what should be the ideal measure from EJscreen?)
   -  Demographics, Ethniticy, Gender Income Variables were provided in SEDA.
   
 Points Raised by Group Members:
   - Esteban: For Causality 
   - Laura: Cons for Causality, maybe looking at associations would be easier.  
   - Wajiha: potential air quality data from non-profit. Looking at Inland Empire 
    
  Future Deliverables:
   -  Project Proposal will be finalized in HackMD link and then transferred to GitHUb.
   
------

`04/21/2021`
 - [x]  **Inclass Group Meeting** 

*Agenda: Brainstroming Session/ Class Discussion*

List of questions generated during the discussion session:
 1. What environmental factors significantly impact educational attainment?
    - Ex. aerosol particulate matter/respiratory hazards
3. In what ways do environmental factors impact educational success?
4. Are minorities and people of color more likely to be affected by environmental toxic exposure? 
5. How should we measure environmental impacts on educational outcomes?
    - Ex. EPA EJ index (does it capture all items that may impact educational outcomes)
7. How do we assess educational outcomes?
    - Ex. Are test scores a good indicator? How do we know if they are being impacted by the environment or something else (ex. SES)
8. Are the current EPA regulations of air pollution control effective? How can they be improve, in order to alleviate the health inpact of children in schools? 
9. Does air quality have the same impact as water quality on educational outcomes?
    - Comparative framework ?? (assessing educational outcomes and types of environmental conditions)
11. Should we look at a comparative analysis of enviroment and how it can potentially impact the school outcome for students in DAC and wealthy neighbourhoods.
12. Does schooling affect environmental outcomes or does environmental outcomes affect schooling?
13. How could land-use policy affect environmental racism for school-age children?
14. How do warehouses impact the environmental toxins in the air near schools? What are the afffects in children? 
15. Looking at environmental risk exposure through school district boundaries (ex. high pediatric asthma in certain school districts; change over time)
-----


  	

