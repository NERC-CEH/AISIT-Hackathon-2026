# AISIT-Hackathon-2026
A repository to store the example notebooks and competition entries for the AISIT Hackathon on the 8th September 2026 at the NERC Digital Gathering held at the University of Stirling.

## The Challenge
Create a Jupyter notebook that identifies and visualises key features of Arctic freshwater flow using the AISIT database and supporting environmental datasets. 

Prizes: Exclusive BAS Merchandise plus broadcasts on AISIT webpages and blogs.

Potential ideas for entries: Predict freshwater source contributions; Detect climate-driven anomalies; Visualise Arctic freshwater pathways; Build explainable AI models linking δ¹⁸O patterns to environmental drivers; Generate decision-support dashboards for researchers… or come up with your own ideas

## How to enter
Fork the repository and create a folder in ```Code``` and a folder in ```Data``` each with the name of your team. Insert your competition code and associated data files in these folders. Don't copy the existing AISIT database, instead read it from ```Data/Common```. Include a ```requirements.txt``` file with the required libraries to run your notebook. 

*Include a comment in the pull request with the names and email addresses of everyone in your team.*

## Specifications

* Your main code base should be hosted in a .ipynb file and able to run entirely without errors from the files including in your pull request. Any language that works in a notebook file is acceptable, but Python or R is preferred.
* In your notebook, alternate code and markdown cells to give your analysis a good narrative structure to make it easy to follow what you are doing and why you are doing it.
* Don't include files larger than 250 MB. Use Git LFS for storage of files above 100 MB. If your code relies on datasets that are larger than this limit, crop the datasets to relevant parameters and/or geographies, or read them directly from online sources within the code.

## Assessment criteria 

Entries will be assessed out of 25 based on the following three criteria: 

* **Technical (/10)**

*The score in this category will be based on the code in your notebook. Entries that score highly will have thoroughly commented code that runs efficiently and can be easily tweaked by the user to change parameters in the analysis. Code should avoid, as far as possible, including large number of software dependencies. If your code involves machine learning or other statistical methods, we will look for application of an appropriate test-train-validate pipeline to the data and error metric (e.g. RMSE or R-squared values). Here we will also assess how well you have integrated the AISIT database into your work (/3).*

* **Scientific (/10)**

*The score in this category will be based on the discussion (in markdown cells) of the code and outputs in your notebook. Entries that score highly will effectively put the results in the context of oceanography, Arctic science and/or isotope tracer analysis. Critical discussion of the relative merits and drawbacks of the approach outlined in the notebook should also be included. If your code involves machine learning or other statistical methods,we will look for a critical discussion of any assumptions your model makes, how much your error assessment can be trusted, and any particular caveats (statistical or oceanographic) as to where your error assessment might be unrealistic.*

* **Scope and innovation (/5)**

*The score in this category will be based on the scope of your work. Entries that score highly will make use of recent developments in data science tools, and include in their analysis datasources beyond the AISIT database (e.g. gridded climate data). If the analysis is predictive, we will look for how ambitious your predictions are in terms of spatial and temporal coverage.*

## Deadline 

Friday 30th October 2026, 9pm GMT. Winner announced on Friday 13th November 2026. 





## Database Correction
After releasing the database, we unfortunately encountered an issue with the depth values of a specific dataset.

The corrections only apply to the **"healy_2016"** dataset and are as follows: 
- Both the "CTD_Pressure_[dbar]" and the "Depth_From_Pressure_[meters_below_surface]" must be replaced with **NaN** values.
- The "Sample_Depth_[meters_below_surface]" and "Combined_Depth_[meters_below_surface]" must be replaced with values of **8**. 

If you're using pandas, we suggest incorporating  the following code into your read in to correct this:
```
mask = df["Dataset"] == "healy_2016"

df.loc[mask, "CTD_Pressure_[dbar]"] = np.nan
df.loc[mask, "Depth_From_Pressure_[meters_below_surface]"] = np.nan
df.loc[mask, "Sample_Depth_[meters_below_surface]"] = 8
df.loc[mask, "Combined_Depth_[meters_below_surface]"] = 8
```
