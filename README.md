# sar-eric-seth
Using synthetic aperture radar (SAR) to study our snowy mountains!

## Name(s) of individual or team members
- Eric Gagliano
- Seth Vanderwilt

## Some introductory background information
- We want to see what information about snow depth, coverage, and other properties we can extract from SAR data
- Advantage of SAR- we can see through clouds, which is great for Washington state/anywhere with stormy winters
- High-resolution SAR imagery will be available soon (Capella Space, ICEYE, ...) and we want to take advantage of this daily/hourly flood of great data!

## Problem statement, question(s) and/or objective(s)
- Can we track snow melt dynamics over a season, especially in WA when have rain-on-snow & other events?
- Does SAR/InSAR give us enough signal to estimate snow depth over time?
  - Can compare CSnow versus S1 RTC AWS public dataset
- Backscatter vs interferograms for our tasks - which are more informative?
  - Snow melt - easy to identify using backscatter imagery
  - Can use phase differences to get at SWE!
  - Snow depth?
- General note: snow is challenging - material properties (water content) affect returns; but possible to extract information with some simple assumptions
- Snow melt dynamics in B.C. with google earth engine (Darychuk et al.) has nice visualizations
- DEM effects - is the same terrain dataset used in processing CSnow at 1km resolution (compromise in order to run globally), how do things compare to running at higher res (say 90m WA state) 

## Datasets you will use (with links, if available)
- [Sentinel-1 SAR on AWS](https://sentinel-s1-rtc-indigo-docs.s3-us-west-2.amazonaws.com/index.html)
  - could use ASF processing (Eric has done)
- UAVSAR? maybe
- C-SNOW through 04/2019
- Grand Mesa data TBD
- WA state data including snotel TBD

## Tools/packages you’ll use (with links)
- Scott Henderson's visualization tool to start https://github.com/scottyhq/sentinel1-rtc
- geopandas
- holoviz tools like HoloViews and Datashader
- [rioxarray](https://github.com/corteva/rioxarray)
- [dinosar](https://github.com/scottyhq/dinosar) (InSAR processing for given area of interest on AWS) if our InSAR analysis is too intensive/too much data to run locally
- [ISCE](https://github.com/isce-framework/isce2)
  - Scott: run topsApp.py for single pair of image SLCs from ASF on UWGDA hub. Run processing in /tmp directory and save final outputs in /merged to your home directory

## Planned methodology/approach
- Start by loading the data & carefully visualizing
- See if we can reproduce some interferograms like [these previews](https://search.asf.alaska.edu/#/?dataset=SENTINEL-1%20INTERFEROGRAM%20(BETA)&zoom=6.204696235854211&center=-143.185674,68.040874&polygon=POLYGON((-148.7149%2069.5738,-143.0713%2069.5738,-143.0713%2070.4726,-148.7149%2070.4726,-148.7149%2069.5738))&resultsLoaded=true&granule=S1-GUNW-D-R-131-tops-20200924_20200831-162716-71174N_69108N-PP-2abd-v2_0_3-amplitude&view=equitorial)
- not sure what else we'll look at yet

## Expected outcomes
- We will have built some reusable tools for SAR processing & visualization that we can keep using in our research group!

## References
- (AGU 2020 Cryosphere session) Darychuk, S.E., et al. Snow Melt Dynamics from Satellite Observations in the Lajoie Basin, British Columbia
- Lievens, H., Demuzere, M., Marshall, HP. et al. Snow depth variability in the Northern Hemisphere mountains observed from space. Nat Commun 10, 4629 (2019). https://doi-org.offcampus.lib.washington.edu/10.1038/s41467-019-12566-y
- Marin, C., Bertoldi, G., Premier, V., Callegari, M., Brida, C., Hürkamp, K., Tschiersch, J., Zebisch, M., and Notarnicola, C.: Use of Sentinel-1 radar observations to evaluate snowmelt dynamics in alpine regions, The Cryosphere, 14, 935–956, https://doi.org/10.5194/tc-14-935-2020, 2020.
  - https://sentinel.esa.int/web/sentinel/missions/sentinel-5/news/-/article/sentinel-1-satellites-observe-snow-melting-processes page broken right now
- https://github.com/isce-framework/isce2-docs/blob/master/Notebooks/UNAVCO_2020/SAR%20Processing/SAR_Processor.ipynb great SAR notebook according to David
- [NISAR science handbook](https://nisar.jpl.nasa.gov/files/nisar/NISAR_Science_Users_Handbook.pdf)
