# Data-visualization-of-Covid-19-for-select arrival-destination travel within USA
Comparing regional data of Covid-19 data from these two locations to visualize spread. 
## __Isaac Johnson__ 
### __Final Project - Data Trends and Visualization with Python__
### Decision Analytics
### EN.663.667 (02)
### 2020.12.18

# Background
Covid-19 virus is strongly speculated to have origins from China and transferred to humans sometime in late 2019. Due to the global interconnectivity of the world today and lack of government action the local outbreak in China quickly became a worldwide pandemic. The USA in particular has experienced bad outbreaks due to variety of reasons e.g. lax travel restrictions in the early months of the pandemic, lack of monitoring for symptoms of incoming people, lack of testing or PPE production during the early deays of the pandemic, and lack of coordinated federal response of US govt towards Covid-19. Additionally, mixed messaging and politicization of practical safety measures exacerbated the spread of the virus, as well as peoples general indifference toward something not directly impacting them. Throughout the year Covid-19 has been unable to be contained with each surge stronger than the last. The baseline heading into the fall was deemed quite high, about 4x higher than preferred levels, and widespread community transmission is now seen in almost all areas of the USA during late autumn/winter season. Due to these conditions its possible many companies or local governments are looking at strongly suggesting or limiting travel during the upcoming winter holidays e.g. Thanksgiving and Christmas/New Years or during 2021 prior to vaccine rollout. While some local governments strongly suggested not traveling for Thanksgiving there was no enforcement of this policy thus many people did travel home. Therfore it's even more prudent to monitor current Covid-19 trends be aware of current guidelines for travel, testing, quarantining etc and try to anticipate impacts on future activities. This project looks at Covid-19 data trends for Maryland and Montana using case incidence, death incidence, and other metrics to examine the current state of Covid-19 outbreak in selected states. It also retrospectively includes a look at the outbreak during July 2020 and attitudes toward masking at that time. The data shows that while they hadd apparently identical outbreaks in July, based on incidence, that currently the outbreak is in an upward trend in Maryland and apparent steep downward trend in Montana. While Montana has a downward trend its incidence still remains above Maryland. Some evaluation of the testing capacity  of each state (e.g. positivity rate) and other data shows practices are quite different between these two states and that this and other factors could be skewing the data - this is expecially the case for Montana. 

# Business/Personal Question
__What are recent Covid-19 virus data trends in regions of travel (Maryland and Montana) and what impact might be some impacts of deciding to travel over the winter holidays?__

# Data Question - Open Data
Data may come from the below sources:
1. __New York Times Covid-19 Data - US Counties and States__: The New York Times provides Covid-19 data, both live and historical, for the Covid-19 epidemic occuring within the USA + territories during year 2020. Data is available on national, state and county level and available data has been tracked since the epidemic started in January. This data comes from reports from state and local health agencies. Due to shortages of tests that were available the data may not reflect full extent of epidemic.
  i. The data used will be historical data. This data does not include results from current day but does include results up to current day. There will be no distinction made between probable cases and/or lab confirmed cases. US state level data can be found [here](https://raw.githubusercontent.com/nytimes/covid-19-data/master/us-states.csv) and county level data can be found [here](https://raw.githubusercontent.com/nytimes/covid-19-data/master/us-counties.csv). 
  ii. __New York Times Covid-19 Data - US mask survey__: NYT commisioned the company Dynata to do a survey on mask usage in time period between July 2nd - July 14th. Survey asked "How often do you wear a mask in public when you expect to be within six feet of another person?" Survey received 250k responses from around the USA. Survey was only collected once. The survey results were weighted by age, gender, and approx location est. by zip code. Estimates of mask wearing were taken by doing a weighted average of the nearest 200 people, with people closest receiving more weight, this was then rolled up to county level data. The raw data for this survey can be found [here](https://raw.githubusercontent.com/nytimes/covid-19-data/master/mask-use/mask-use-by-county.csv).
2. __Press releases from state and local authorities__: These posts will be sourced from government websites or local websites where the executive orders or briefings are made available. The City of Baltimore Executive orders can be found [here](https://www.baltimorecity.gov/executive-orders), Maryland state press briefings can be found [here](https://governor.maryland.gov/coronavirus/), newest exectute order issued on 2020.12.16 from Governor Hogan was found [here](https://governor.maryland.gov/2020/12/17/home-for-the-holidays-governor-hogan-announces-new-travel-orders-180-million-more-in-economic-relief/) updates on status of reopening in Montana can be found [here](https://covid19.mt.gov/joint-information-center), and information on Butte, MT can be found at county level by looking at Silverbow county data [here](https://www.co.silverbow.mt.us/2167/COVID-19).
3. __Technical Definitions__:The data is organized geographically by Federal Information Processing Standards [FIPS](https://www.census.gov/library/reference/code-lists/ansi/ansi-codes-for-states.html) State Numeric Codes. In this case we are concerned with Maryland (FIPS - 24) and Montana (FIPS - 30). [County level](https://www.nrcs.usda.gov/wps/portal/nrcs/detail/national/home/?cid=nrcs143_013697) FIPS data is available here. This allows the analyst to look at specific regions of travel e.g. Baltimore City (considered county equivalent), Silverbow County (Butte, MT).
4. The __original files__ can be accessed on google drive [here](https://drive.google.com/drive/folders/1PQV6Ak1Q677Mj3mM3kVnflpcUmFzW9Bn?usp=sharing), and the edited files can be found within the Google Collaboratory notebook. Links are open access. 
5. Covid-19 Testing sites found from using Google map search and [MT Covid-19 testing sites](https://covid19.mt.gov/Montanas-Testing-Information)
6. __United States Census Bureau__ Data used for state map shapes, cartographic boundary files from year 2018, can be found [here](https://www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.2018.html). For county level a JSON type file should be used, not done in this analysis, but can be found [here](https://raw.githubusercontent.com/plotly/datasets/master/geojson-counties-fips.json)
# Data Question - Analysis
Google Collaboratory was primarily used for data analysis with Excel for pie charts.
* **2020-12-18-Data visualization-Covid-19-data-mainland-USA-IJ.ipynb**:
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1x5RL8Xem-qcrM2Gn2yRchTNPzH44BaXi?usp=sharing)
Or see saved copy in Github Repository

- __What has the previous month's trend been in terms of covid cases?__ This will look at daily cases at state level to see whether the region is entering danger zone and look at daily cases, 3-day-average,and [incidence](https://www.cdc.gov/coronavirus/2019-ncov/downloads/global-covid-19/SARS-CoV-2-Transmission-Metrics.pdf) defined as "the occurence of new cases of a disease over a specified period of time" and mathematically defined as ((number of new cases of disease during specified period)/(by size of population at start of period)) * 100,000 gives you cases per 100,000 population. By using incidence can compare different regions. The population size is based on census data last taken in 2010 found here for [Montana](https://www.census.gov/prod/cen2010/cph-2-28.pdf), [Maryland](https://www.census.gov/prod/cen2010/cph-2-22.pdf). The data from NYT is reported in terms of __cumulative__ cases so daily difference must be taken to get daily new cases. Sometimes a person is later reclassified to different county, state etc so this explains a decrease in cumulative cases over time that may occur throughout data. 
- __What is the previous month's trend for deaths?__ This will look at daily reported deaths, 3-day-average, and 3-day-incidence to provide idea about whether state/county health agencies are in danger of being overwhelemed.The Department of Health and Human Services (HHS) provides state level data on this [here](https://healthdata.gov/dataset/covid-19-estimated-patient-impact-and-hospital-capacity-state). 
- __What have been the previous month's recommendations from Governor or Mayor?__ This will provide an idea of how proactive government agencies are being at handling pandemic and allow for travel/post travel plans to be made so that the spread of Covid-19 can be limited and travel can be conducted safely or with minimized risk.
__Retrospective look at cases in July 2020 and attitudes toward mask usage then__ This may provide some insights into culture of the travel destinations and possibly reason for current status of outbreaks in each place.

# Data Answer
## Trends in daily covid cases
First the daily covid cases for past 30 days were examined for Maryland and Montana. This provides some surveillance of the landscape we're going to potentially be interacting with. Maryland and Montana have vastly different population sizes with Maryland population estimated as 6 million while Montana population is estimated as ~ 1 million. Th land masses are also quite different with Maryland being about 8.5% the size of Montana indicating high differences in population density. 
Maryland daily cases close to tripled over the duration of the month from 1k to 3k. For Montana daily cases appear to have peaked in mid November at about 1600 but are now down to similar levels observed at the beginning of the month of about 800 cases per day. 
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Fig1_dailycases_MD.png)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Fig2_dailycases_MT.png)

Similar trends as observed in the daily cases were observed in the 3-day average and the 3-day incidence which stands at about 40 right now, up from 15 at the beginning of the month. Similar trend is observed with incidence. The initial incidence rate at beginning of November was about 80, it peaked at about 130-140 mid month and has fallen back to 80 as we head into December. The 3 day incidence of MT is mucher higher than Marylands suggesting death incidence will remain higher for the near future as well. Based on incidence trends here both states are in the red zone since their level is > than 25 daily new cases per 100k people. Maryland transitioned from the orange zone into the red zone over the past month, while Montana has maintained its status as deep red over the course of the past month. Current outlook is that community transmission will continue to be an issue in both states. According to the CDC, the 3-day incidence number can be used to determine whether illnesses in the area are increasing, decreasing, or stable. Depending on the incidence level its possible to know the threat level of the region with [classifications](https://ethics.harvard.edu/files/center-for-ethics/files/key_metrics_and_indicators_v4.pdf) as follows: green (< 1 daily new case per 100k), yellow (< 10 daily new case per 100k), orange (10<25 daily new case per 100k), and red (> 25 daily new case per 100k).  
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Fig3_3dayaverage_MD.png)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Fig4_3dayincidence_MD.png)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Figure5_3_day_avg_cases_MT.png)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Figure6_3_day_incidence_MT.png)

## Trends in 3 day average of deaths
The 3  day death rate for Maryland and Montana are shown below in Figure 7-10. Figure 7 and 8 show the data for Maryland as a 3-day average and normalized for population, similar data is shown in Figure 9 and 10 for Montana. During the month of November the death rate has steadily risen. For Maryland, the beginning of November showed 3-day average of 5-10 deaths, that has now risen to 20-30 deaths with more expected. The incidence rate showed similar magnitude of increase rising from about 0.1-0.2 to ~ 0.5 deaths per 100k calculated on a 3 day average basis. For Montana 3-day average of deaths has doubled over the course of the month, rising from approx 8 to 16. The data is more choppy with no clear rise over the past month. When we look at the incidence rate though it tells a different story. The incidence at the beginning of the month was about 0.8 and was between 1.4-1.6 for the majority of the month. This suggests the outbreak is being handled much worse than in Maryland given that the incidence deaths are 2-3 times higher. Montana is a sparsely populated state. It does not have comparable resources to Maryland and would likely have not made similar investments in public health as Maryland nor have the same testing or hospital capabilities to tolerate a severe outbreak. 
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Fig7_3day_deaths_MD.png)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Fig8_3day_death_incidence_MD.png)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Fig9_3day_deaths_MT.png)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Fig10_3day_death_incidence_MT.png)

## Results of mask survey for Baltimore, MD and Silver Bow County, MT - July 2020
A retrospective examination of 3-day case incidence for Montana and Maryland were done and mask usage was examined for Baltimore and Silver Bow County. The results, shown below showed that during that time period both states had similar outbreak levels. Incidence rose from single digits 5-6 cases per 100k to about 16 over the course of the month. Survey results showed Baltimore City residents were much more likely to wear a mask with respondents indicating they wore a mask always when outside and around people 73% of the time, while for Silver Bow county this number was only 50%. Perhaps more concerning were the number who said they wore a mask rarely or never. For Baltimore City the number of people who never wore a mask was 2.4%, and rarely (assumed less than 20% of the time by study) was 3.2% while in Silver Bow those numbers were 15.8% (never) and 13.8% (rarely). That's a staggering difference in attitude. While the populations and sizes of each dates are quite different, as mentioned above, this appears to have not benefitted MT which should have had some advantages due to low population and massive size. This also holds true for the compared cities here. Baltimore has a population of about 620961 while Silver Bow county has population of 30093. Yet despite these differences Maryland currently has an incidence of about 40, a positivity rate of ~ 8% while Montana's incidence is closer to 50 and Silver Bows local positivity rate is ~ 16%. One caveat is that the testing situation is vastly different in these two states. Shown in a section below is testing sites in Montana vs testing sites just around Baltimore City. Additionally, many of the testing sites in MT have restricted access. This indicates outbreak reporting is likely being underreported and true toll is far worse.
![alt text](https://github.com/ijohns29/Data-visualization-of-Covid-19-for-mainland-USA/blob/main/Mask%20usage%20Baltimore%20City.JPG)
![alt text](https://github.com/ijohns29/Data-visualization-of-Covid-19-for-mainland-USA/blob/main/Mask%20usage%20Silver%20Bow%20County.JPG)

## Additional data on Maryland region
Here we can see recent trends positivity rate for under and over 35 age groups as well as any changes in the state's testing volume over time. For younger people the positivity rate at the beginning of the month was higher than for older people at a value of 4.68%, and that value remains higher than older people's at the end of the month as well, at a value of 8.31%. For older people the positivity rate at the beginning of the month was 3.78%. Its almost doubled since then and stands at 7.31% now. The data shows that both age groups saw large increases in positivity rates though the older age group's was slightly larger. Positivity rate is trending upward as we start December. It seems likely to increase as the infections from Thanksgiving travel become realized. The testing volume levels are fairly consistent across the month, with more tests typically processed on the weekend, whether this a result of more people being tested at the end of the week or due to something else is unknown.      
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Fig11_pos_rate_under35_MD.png)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Fig12_pos_rate_over35_MD.png)
![alt text](https://github.com/ijohns29/Comparing-regional-Covid-19-data-trends-in-MD-and-MT-to-assess-short-term-risks-of-travel/blob/main/Fig13_testingvolume_MD.png)
## Baltimore Covid-19 Testing sites
![alt text](https://github.com/ijohns29/Data-visualization-of-Covid-19-for-mainland-USA/blob/main/Baltimore%20Covid-19%20Testing%20Sites.JPG)
## Montana Covid-19 Testing sites
![alt text](https://github.com/ijohns29/Data-visualization-of-Covid-19-for-mainland-USA/blob/main/Montana%20Covid-19%20testing%20sites.JPG)
## Airport Safety Precautions
1. Currently BWI airport has a number of administrative controls in [place](https://www.bwiairport.com/COVID19socialdistancing) to minimize spread of Covid-19. These include all restuarants at 50% capacity, social distancing and masks required, as well as various plexiglass installments at high traffic areas (e.g. security, airline counters, checkout lines etc.). Currently the government of the state of Maryland, and posted on the BWI [airport](https://www.bwiairport.com/COVID19socialdistancing) strongly discourages travel to areas with incidence equal to or greater than 20 per 100k.  
2. [BTM](https://co.silverbow.mt.us/2167/COVID-19) listed basic conditions such as mask wearing and hygiene but no other engineering controls were mentioned. They did include latest update on local Covid-19 status, local restrictions in place and most recent state goal i.e. getting 7 day incidence below 25 per 100k for two weeks.
The [Maryland Department of Health](https://phpa.health.maryland.gov/Documents/2020.11.10.03_MDH_Advisory_Large_Gatherings_Travel_Long_Term_Care_Visitation.pdf) recently issued guidance for travelers from Maryland. They recommended all Maryland residents returning from out of state get tested for Covid-19 within 72 hours of their departure from their out of state destination. Furthermore it is recommended they quarantine while awaiting their test results. Secondly, any Marylander who travels to state with Covid-19 rate greater than or equal to 20 per 100k (in past 7 days of their visit) should be tested and quaratine at home until results have been received.  
3. Recent press releases from the Governors's office for Maryland indicate medical staffing are being surged in to bolster the increased hospitalizations resulting from increased cases and police and local authorities are engaged in movement to promote compliance with Covid-19 guidelines as well as penalize those who blatantly disregard them.
# Business Answer
Using this data analysis the company personnel can examine regional trends regarding Covid-19 outbreak and assess the level of risk that the employee may be subjecting themselves to during their travel. The manager should be aware this data analysis may not indicate emerging outbreaks as these tend to flare up suddenly. Furthermore this assessment does not make any assumptions regarding employee behavior during travel, which will likely be the largest factor that will impact Covid-19 risk. It's recommended that travel be approved or rejected based on trends and local guidance and then reassessed within one week of departure date to see how the outbreak has evolved and plans adjusted accordingly. Organizational guidance regarding holiday travel can be found [here](https://hub.jhu.edu/2020/10/20/covid-19-winter-holidays/?mc_cid=295c6bc1e2&mc_eid=4aff72f931). Based on available data presented above travel is strongly discouraged within both states as Covid-19 incidence are in red zone for both departure and arrival states. Should travel occur the indivual should test before leaving and after arrival to destination, as well as upon return. The individual should quarantine at residence until results of testing are known suggesting travel for business is not recommended unless it will be an extended stay. It's strongly recommended that people traveling for business follow all local regulations regarding Covid-19 protocol. 
This project feeds in data much more smoothly than excel. Once the framework is built its very easy to update and grab the latest data and swiftly incorporate it into existing visuals and dataframes. With regards to improvements that could be made I should feed in more local data on Montana. I primarily included additional data on MD as it was easily accessible. In future I'd like to update the visuals more. Currently its bar graphs which while functional and easy to understand are a little boring. I should include hospital data next time as it illustates how close the public health system is to breaking down. Typically less than 15% capacity and there's some large concerns about the harsh restrictions being imposed in order to regain control and preserve public health system capabilities. 
