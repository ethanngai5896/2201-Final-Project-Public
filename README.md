Read me for INFO 2201-301 Final Project
Made by Noah Southworth and Ethan Ngai


Notes on Data Source
1. Where are you getting it from? 
First starting this project, I first looked for apis that had data in relation to the Corona virus. I came across a repository on Github that had what I wanted to look more into. (https://github.com/CSSEGISandData/COVID-19) Once I found the repository, I downloaded the zip file associated with it. The zip file contained global and US corona virus data. I chose to use the Global deaths and confirmed cases data, which was taken from the Johns Hopkins Coronavirus Resource Center (https://coronavirus.jhu.edu/map.html). 

2. What data type is it? The two files I used for this project were csv files. These contained information from an excel sheet. 

3. What are the restrictions of that data type (gaps? Ethics?) There was one factor in this project that restricted me. The 3 files I wanted to use was Confirmed Cases, Death Cases, and Recovered Cases. However, the Confirmed and Death cases were reported up to 3/9/23. But, the Recovered Cases only reported up to 1/9/22. This disabled me from using this data and comparing it to the other two sources. As well as, the Johns Hopkins Website stopped updating its information back in 3/10/23. This is a little challenging, as this was almost a year prior, and I could be missing relavant information within the past year. Thinking about the ethics of this data type; there was no breach in ethics. All health and personal information has not been included. As well as, accessing this data is ethical, as "this website is a resource to help advance the understanding of the virus, inform the public...improve care, and save lives."

4. Pros and Cons of this data source in terms of accessibility?
CONS: API hard to understand, navigating the zip file was difficult, data source was extreme; data was taken from 200+ countries, each country doccumenting about 3 years. Navigating and cleaning data file was difficult (in terms of size). The data source itself had information that was not needed, as well as had to be reformatted for visualization. Visualizing the data source was difficult, as we needed to import python functions in order to look at the data as a whole. 

PROS: This data source was in csv format, so I could easily import it into a notebook using the notes. There was not much data to pick from in zip file, data utilized was clear and understandable. For me, one pro of this data source was that it was in an excel sheet, so I could look at it and determine the column names and visualize what I was looking at. Once formatted in the way that was needed, it was easy to iterate through the columns and the data for each country as a whole. The biggest help in this data source, in terms of accessibility, was that it was formatted the exact same way, word for word, data for data. I just had to clean one, and copy the code I did and repeat the process for the other data source. 


Walk Through of Data Pulling
1. Where did you get it from? I got the data used in this project from a old repository from github (https://github.com/CSSEGISandData/COVID-19). This repository pulled data from the Johns Hopkins Coronavirus Resource Center page (https://coronavirus.jhu.edu/map.html). 

2. How did you get it? I got the data used in this project from downloading an old repository from Github. The downloaded repository was made into a zipfile, which I had to unzip and look at. The 2 csv files used in this project was found in this zipfile. Once I found the 2 csv files, I downloaded them and imported them into jupyter notebook. This was then where I wrote code to open and look at the two files. 


Walk Through of Data Cleaning
1. What choices did you make?
- First, I looked at the file as a whole, and realized what bits I did not need. For example, when looking at the confirmed cases global, the data source contained the province/state for each country/region. It also contained the exact latitude and longitude for each country/region. I wanted to just have 'Country/Region', 'Dates', and 'values (cases)' I used the .drop function and removed these. 
-Second, after deleting what was not needed, I realized that I still had to combine data. For example, China has 22 provinces, and when I deleted the 'Province/State' column, I still had the 'Country/Region column' containing 22 instances of China. I decided to take these multiple instances in the 'Province/State' column, group them, aggregate the data for them, sum the aggregate into 1 'Province/State'. Next I flipped the dataframe to have each country/region as its own columnname, instead of date.
- Third, after flipping the data frame, I had to create a new column name for the dates on the y axis. I did this by specifying the indexname of the data set and resetting the index
-Forth, I decided to take each country (which was a column name) and format it into its own column with each country being a row. This would create three column names (Date, Country/Region, and values) which is the format I wanted to have to visualize from using the .melt() function to reshape my country/region column name into a long table, with each row being a country.
-Fifth, once the data set was formatted in the way I wanted, I just had to rename the 'Value' column to the name I wanted. That being 'Confired' or 'Deaths'
-sixth, the next thing I had to do was convert the date format. the date was represented as a string, which would have been hard to code with, so instead I changed the format to date/time. (when finding max date using .max() function, pandas would find the wrong date because of the string format).


2. What was selected/Deleted? I chose to delete the'province/state' of each country, and I deleted the logitude and latitude of the country/region.

3. Why? Well, First I deleted the province/state of each country because it would have been confusing having to share the 6+ regions of china and each of their data sets. I wanted it to be simplified, and so I just combinded the provinces of the country as one. Next, I deleted longitude and latitude because it was not helpful to my project



Reflection on Visualizations
1. What makes the visualizations captivating is the large margin between the United States and the four other countries regarding the number of confirmed cases of and deaths from COVID-19. Over 100 million of the United States' 333 million population has contracted the virus since 2020. Meanwhile, India, the next country on the list with a population of over 1.4 billion, had over 40 million cases. Our higher number of confirmed cases is not due to population number alone, as India's numbers prove by their ratio of cases to population being roughly one-tenth of ours.

Adding to this frightening statistic is the trend present in the graphs. For most countries, deaths related to COVID-19 began to level off around February of 2022, but deaths due to COVID-19 in the United States continued to rise.

Storytelling/Insight
1. Where is this helpful? What should other people draw conclusions about from your visuals and cleaning?
This begs the question: Why do we have such a disproportionate number of COVID-19 cases and deaths? While we can make educated guesses as to reasons behind it, such as the political landscape at the time, which led to medical doubt and speculation; As well as the fact the United States waited until 3,000 national cases were confirmed to initiate the lockdown, while India began its lockdown at just 500. These situations rarely have only one reason behind them. 
Despite this, we can still use this broad-stroke picture to improve our existing systems. The past four years have taught us that our current procedures for massive epidemics are inadequate, and looking at exactly where we failed will hopefully bring about policy changes that may help mitigate the damages done to people when the next pandemic comes around.
