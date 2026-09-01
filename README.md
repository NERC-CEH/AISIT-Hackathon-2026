# AISIT-Hackathon-2026
A repository to store the example notebooks and competition entries for the AISIT Hackathon on the 8th September 2026 at the NERC Digital Gathering held at the University of Stirling.

## The Challenge
Create a Jupyter notebook that identifies and visualises key features of Arctic freshwater flow using the AISIT database and supporting environmental datasets. 

Prizes: Exclusive BAS Merchandise plus broadcasts on AISIT webpages and blogs.

Potential ideas for entries: Predict freshwater source contributions; Detect climate-driven anomalies; Visualise Arctic freshwater pathways; Build explainable AI models linking δ¹⁸O patterns to environmental drivers; Generate decision-support dashboards for researchers… or come up with your own ideas

## How to enter
Fork the repository and create a folder in ```Code``` and a folder in ```Data``` each with the name of your team. Insert your competition code and associated data files in these folders. Don't copy the existing AISIT database, instead read it from ```Data/Common```. 

*Include a comment in the pull request with the names and email addresses of everyone in your team.*

## Specifications

* Your main code base should be hosted in a .ipynb file and able to run entirely without errors from the files including in your pull request. Any language that works in a notebook file is acceptable, but Python or R is preferred.
* In your notebook, alternate code and markdown cells to give your analysis a good narrative structure to make it easy to follow what you are doing and why you are doing it.
* Don't include files larger than 250 MB. Use Git LFS for storage of files above 100 MB. If your code relies on datasets that are larger than this limit, crop the datasets to relevant parameters and/or geographies, or read them directly from online sources within the code.


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
