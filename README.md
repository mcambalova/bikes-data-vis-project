# Bike Sharing: Data Visualization Project
## by Maria Cambalova


## Dataset

The [Ford GoBike system data](https://www.lyft.com/bikes/bay-wheels/system-data) for the two years 2017 and 2018 is explored using various visualizations (univariate, bivariate and multivariate). One row (record) is one bike ride, and it is anonymized. The data contains following features:
- __trip duration__: total duration of one ride in seconds
- __start date and time__: time and date when the ride started
- __end date and time__: time and date when the ride ended
- __start station ID__: start station identifier
- __start station name__: name of the start station
- __start station latitude__: the latitude coordinate of the start station
- __start station longitude__: the longitude coordinate of the start station
- __end station ID__: end station identifier
- __end station name__: name of the start station
- __end station latitude__: the latitude coordinate of the end station
- __end station longitude__: the longitude coordinate of the end station
- __bike ID__: the bike identifier
- __user type__: whether the user is a regular one, i.e. member ('Subscriber') or a casual one ('Customer')
- __Bike Share for All__: whether the ride was within the [Bike Share for All](https://www.lyft.com/bikes/bay-wheels/bike-share-for-all) program, not available for 2017 rides<br>

Before exploration, preliminary wrangling was performed:
- all required files (one for 2017, 12 for 2018) were downloaded and loaded into a Pandas dataframe
- start date and time column was converted to datetime datatype to extract year, month, day, day of week, and hour
- user type, created month and day of week columns were converted to categorical variables
- duration in seconds was converted to duration in minutes
- unnecessary columns not used in the subsequent explorations (start and end date and time, start and end station ID, start and end station latitude and longitude, bike ID, Bike Share for All, duration in seconds) were dropped afterwards  

The final dataset is stored in .pkl format zipped in [bike_shares_master.zip](/data) and contains following columns:
- __start_station_name__: the name of the start station
- __end_station_name__: the name of the end station
- __user_type__: same as above (subscriber/costumer)
- __year__: year (2017 or 2018)
- __month__: month name (January, February, ... December)
- __day__: day in month (from 1 to 31)
- __weekday__: day in week (Monday, Tuesday, ... Sunday)
- __hour__: hour in day (from 0 to 23)
- __duration_min__: trip duration in minutes  


## Summary of Findings

Data from 2017 is incomplete, because the bike-sharing service started only in the second half of the year (more precisely, in June, but the number of users was very low in this month). The number of rides has been gradually increasing through 2017 and continued to increase in 2018, demonstrating the increasing popularity of this transportation solution.  

__Trip duration__  
The most of trips are short - trip duration follows a unimodal distribution centered at around 5-15 minutes, and is positively skewed even after logarithmic transformation. When looking at the trips' lengths at different levels of detail, some interesting patterns are revealed:
- longer trips including the weekend ones are made by casual customers in all months
- subscribers' trips tend to take approximately the same time irrespective of the day and month, and are shorter than customers' trips  

It would be nice to bring these findings into the explanatory presentation, and I'd opt for bivariate or multivariate plots to show them in a complex way.  

__The number of rides__  
The univariate, bivariate and multivariate visualizations revealed following:
- with respect to month, the highest number of rides happen from May to October 2018. As for 2017, the year the service started to operate, the usage of shared bikes increased from June to October, then it dropped a little bit, and continued its growth in 2018. It seems that season doesn't play a vital role for the bike-sharing business, probably due to the climate conditions - see [San Francisco on Wiki](https://en.wikipedia.org/wiki/San_Francisco#Climate).
- day of week is much more decisive - the busiest days are week days (Mondays, Tuesdays, Wednesdays, Thursdays and Fridays), irrespective of the month, and the least number of rides occurs on weekend days (Saturdays and Sundays)
- time of day (hour) is also a crucial factor - there are two peaks representing elevated bike-sharing service usage on week days corresponding most likely to peoples' rides to and from work or school. There are no such peaks on weekends.
- findings described above depend on whether the user is subscriber or not. Because the majority of users (in both years) are subscribers, the patterns observed for all users' rides mirror the subscribers' patterns such as the two strong week day peaks and less popularity on weekends. However, when the data is divided into subscribers and customers, customers' rides patterns are revealed - there are still these week day peaks, but there are more rides during weekends comparing to the rest of the week.  

I'd like to combine the created bi- and multivariate visualizations to illustrate the above described findings.  


## Key Insights for Presentation

Trip duration and the number of trips depends on several factors including the time of day, day of a week, and whether the user is a subscriber or not. I've chosen various visualizations using various level of detail to document the findings in a logical way.  


## Resources

Here is a list of resources used when working on the project:

- Numpy's zfill method documentation: [zfill](https://numpy.org/doc/stable/reference/generated/numpy.char.zfill.html)
- Usage of the Numpy's zfill method described in a post: [Adding leading zeros to strings in NumPy array](https://stackoverflow.com/questions/55376333/adding-leading-zeros-to-strings-in-numpy-array)
- Zipfile module documentation: [zipfile](https://docs.python.org/3/library/zipfile.html)
- Usage of zipfile in a post: [Unzipping files in Python](https://stackoverflow.com/questions/3451111/unzipping-files-in-python)
- Glob module documentation: [glob](https://docs.python.org/3/library/glob.html)
- Documentation of datetime properties to obtain date and time portions: [Datetimelike properties](https://pandas.pydata.org/pandas-docs/stable/reference/series.html#datetimelike-properties)
- Pandas to_pickle() and read_pickle() method documentation:
    - [to_pickle() method](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.to_pickle.html)
    - [read_pickle() method](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_pickle.html)
- Ford GoBike on Wiki: [Bay Wheels](https://en.wikipedia.org/wiki/Bay_Wheels)
- San Francisco on Wiki: [San Francisco](https://en.wikipedia.org/wiki/San_Francisco#Climate)
- A post on combining multiple lists into a dataframe: [Take multiple lists into dataframe](https://stackoverflow.com/questions/30522724/take-multiple-lists-into-dataframe)
- A post on colorbar: [One horizontal colorbar for seaborn heatmaps subplots and Annot Issue with xticklabels](https://stackoverflow.com/questions/45122416/one-horizontal-colorbar-for-seaborn-heatmaps-subplots-and-annot-issue-with-xtick)
- Posts helpful when creating the explanatory visualizations:
    - [Hiding axis text in matplotlib plots](https://stackoverflow.com/questions/2176424/hiding-axis-text-in-matplotlib-plots)
    - [Figure Title](https://matplotlib.org/3.1.1/gallery/subplots_axes_and_figures/figure_title.html)
    - [Multi Image](https://matplotlib.org/gallery/images_contours_and_fields/multi_image.html#sphx-glr-gallery-images-contours-and-fields-multi-image-py)
    - [matplotlib: colorbars and its text labels](https://stackoverflow.com/questions/15908371/matplotlib-colorbars-and-its-text-labels)
    - [Top label for matplotlib colorbars](https://stackoverflow.com/questions/33737427/top-label-for-matplotlib-colorbars)
    - [Matplotlib tight_layout() doesn't take into account figure suptitle](https://stackoverflow.com/questions/8248467/matplotlib-tight-layout-doesnt-take-into-account-figure-suptitle)
    - [Rotate tick labels in subplot (Pyplot, Matplotlib, gridspec)](https://stackoverflow.com/questions/31186019/rotate-tick-labels-in-subplot-pyplot-matplotlib-gridspec/52461208)
    - [Python xticks in subplots](https://stackoverflow.com/questions/19626530/python-xticks-in-subplots)
- lessons learnt in the Data Wrangling part of Data Analyst Nanodegree Program at Udacity  

Note: Common libraries such as NumPy, Pandas, Seaborn and others are not listed here. 
