---
name: Homework 5
tools: [Python, HTML, vega-lite]
image: assets/pngs/cars.png
description: This is a "showcase" project that uses vega-lite for interactive viz!
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---


# Homework 5

The visualizations below use the [UFO dataset](https://github.com/UIUC-iSchool-DataViz/is445_data/raw/main/ufo-scrubbed-geocoded-time-standardized-00.csv).  

## Visualization 1

<vegachart schema-url="{{ site.baseurl }}/assets/json/chart1_hw5.json" style="width: 100%"></vegachart>
This is a plot of UFO sighting durations (in seconds) over time. I initially tried to plot the actual sightings out,
using a scatter plot, but ultimately the gap between the longer and shorter durations made for a less-than-
insightful chart. I ended up displaying the max, min, median, and mean for each year in log,
which obscures the amount that occur each year but at least gives an impression of the range and 
variety of reported experiences. I think that it reveals some interesting insights, like the fact that the 
median duration flattens out around 1950.

Colors are default because selected colors wouldn't give additional meaning. Both duration is encoded
as quantitative. I tried both temporal and quantitative for the year and it led to weird x-axes
with the former not displaying correctly at all and the latter expanding back and forth beyond the start date.
Ultimately, the order defined in ordinal encoding worked better for this plot. 

__Note:__ This doesn't look great on this page! All the years are scrunched in a way that didn't occur in
the notebook. My apologies for the unpleasant x-axis.

## Visualization 2

<vegachart schema-url="{{ site.baseurl }}/assets/json/chart2_hw5.json" style="width: 100%"></vegachart>

This is an interactive plot that allows the user to select a state and see the count of the appearances of
each UFO shape in sightings that occurred in that state. State selection is done by the state initials
(as per the original file.) The chart has been coded to show all the shapes in a consistent alphabetical
order so it is easier for the user to make comparisons between states. For example, the fact that Illinois
has no accounts of pyramid or delta shaped UFOs wouldn't be as obvious without this small modification. When this
is charted without a selector, i.e., so all the states display at once, you get data that is too busy 
to interpret and with gaps in numbers wide enough that states with smaller populations like Vermont
are totally overshadowed.

The shape is encoded as nominal, the default for string data. Count is quantitative, since, well, most
counts are quantity-based. Utlimately this has the default color scheme; more iteration could make it more obvious
how much each bar represents (since it changes per state based on the data available), and using a graduated
schema could be part of that process. 