# How has the Tour de France changed in the last 100 years?
Cycling's premier event has become shorter, hillier and faster paced since it began more than a century ago.

## DATA
Data analysis can be found in analysis.ipynb

| Filename | Description |
| :----------- | :----------- |
| k-stage_data.csv | Data on riders for each stage |
| k-tdf_stages.csv | Data on the stages |
| k-tdf_winners.csv | Data on the winners |

## k-stage_data.csv (1903-2019)

| Name | Description |
| :----------- | :----------- |
| edition | Edition of race |
| year | Year of race |
| stage_results_id | Stage ID |
| rank | Rider rank for the stage |
| time | Time of rider |
| rider | Rider name |
| age | Age of rider |
| team | Team name |
| points | Points for the stage |
| elapsed | Time elapsed |
| bib_number | Bib number |

## k-tdf_stages.csv (1903-2017)

| Name | Description |
| :----------- | :----------- |
| Stage | Number of stage |
| Date | Date of stage |
| Distance | Distance in kilometers |
| Origin | Stage start city |
| Destination | Stage end city |
| Type | Type of stage |
| Winner | Winner of the stage |
| Winner_Country | Winner nationality |

## k-tdf_winners.csv (1903-2019)

| Name | Description |
| :----------- | :----------- |
| edition | Edition of the tour de france |
| start_date | Start date |
| winner_name | Name of the winner |
| winner_team | Team of the winner |
| distance	Type | Distance in kilometers |
| time_overall | Time in hours |
| time_margin | Difference between race winner and runner up |
| stage_wins | Number of stage wins |
| stages_led | Number of stages spent as the race leader wearing the yellow jersey by the eventual winner |
| height | Height in meters |
| weight | Weight in kilograms |
| age | Age of winner |
| born | Year of birth |
| died | Year of death |
| full_name | Full name |
| nickname | Nickname |
| birth_town | Town of birth |
| birth_country | Country of birth |
| nationality | Nationality |

## RELEVANT FIGURES

### Length of Tour de France 1903 v. 2019
- Converted kilometers into miles by multipling by 0.621371

### Percent change in hilly or mountainous stages
### Percent change in flat or plain stages
- Simplified the naming of the categories
- Added a decade column
- Grouped years into decades, 1900-1909, 1910-1919 etc.
- Summed each type of terrain by decade
- Did a percent change calculation compare 1990s to 2010s using ((v2-v1) / v1) * 100
- Dropped the "Other" category as it was often 0 or less than 1 percent

### Percent of type of stage by decade
- Added decade column
- Grouped years into decades, 1900-1909, 1910-1919 etc.
- Number of times the stage appears / total number of stages that year

### Average speed of winning rider in 1903 v. 2019
- Calculate percent change in average speed by using ((v2-v1) / v1) * 100
- Convert the kilometers per hour into miles per hour by multipling by 0.621371

### Average speed of winning rider by decade
- Added a decade column
- Grouped years into decades, 1900-1909, 1910-1919 etc.
- Converted kilometers into miles by multipling by 0.621371

### Name, age, country of youngest modern-era Tour de France winner
- "Modern-era" is 1990-present
- Extracted from Tour de France website directly, would have liked to scrape 2018-present data into a smaller CSV and merge it into the larger dataset

### BMI
- Weight / Height ^2

## CHARTS

### Uphill climb for Tour de France riders
https://app.datawrapper.de/archive/team/theledeprogram/https://www.datawrapper.de/_/qLZ5i/

### Pace of the peloton picks up: 
Line chart: https://app.datawrapper.de/archive/team/theledeprogram/https://www.datawrapper.de/_/aRsTN/

Horizontal bar graph: https://app.datawrapper.de/archive/team/theledeprogram/https://www.datawrapper.de/_/cq8HD/

#### To create the graphic in Illustrator
- Created the horizontal bar chart and line chart in Datawrapper
- Exported the charts as SVGs into Illustrator
- Imported an image of a cyclist from The Noun Project into Illustraor
- Appended the image the ends of each of the 12 bars
- Grouped the images and aligned them to the bottom to make one single-file row
- Removed the labels from the line chart and turn it into a sparkline with labels for both the starting and endpoint year and speeds displayed as an annotation
- Removed the labels from the bar chart as there were two different scales
- Created two guidelines for the start and end of the pictogram and increased the size of the grouped SVGs to align with the start and endpoint of the sparkline.
- Changed the fill of all images the middle points on the pictogram to grey

## WHAT I LEARNED / CHALLENGES
- The Tour de France website does not have an easy way to download all historical data as a CSV: https://www.letour.fr/en/history
- The map of the full course with all the segments combined together is only available in PDF format.
- Generic information about the route for this year's Tour can be found in a table on: https://www.letour.fr/en/overall-route
- Each stage of the Tour has its own page, i.e. https://www.letour.fr/en/stage-1
- Each segment is presented in a small map using ESRI, but can only be downloaded as an image not as a SHP or KML file
- Reuters, The Guardian were among the few newsrooms to have the individual segments.
- The Strava segments do not match the actual course presented on ESRI.
- Others have attempted to scrap the entire, but many repositories were in R: https://github.com/alastairrushworth/tdf
- There are purportedly some errors in the data presented on the official Tour de France website
- Did manage to find a scraped dataset as a CSV that I imported into Jupyter Notebook from Kaggle: https://www.kaggle.com/datasets/pablomonleon/tour-de-france-historic-stages-data
- Elevation data for each of the stages is not available and requires a third-party tool such as GPS Visualizer
- The types of stages and how they are named changed over the years, which needed to be simplified for the line chart
- Was missing data for 2018-present in some of the CSV files

## OTHER NOTES
I'm still unclear in Pandas how to do the following:
- Groupby and then filter by a specific column
- When to use dropna in order to remove NaN values
- A more efficient way to group by decade from timestring start point
- Knowing what I know now, I would have liked to try scraping the Tour website myself with BeautifulSoup