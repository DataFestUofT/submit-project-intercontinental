# An Analysis on Canada's social distancing during COVID-19

1st Place in Best insight, ASA Datafest@UofT

Team Intercontinental's official repo 


## Project Background Story

On May 31st, more than two months into nationwide lockdown, my friends and I decided to go to the Harbourfront for a walk. With our face masks on, we were excited to get some fresh air through our stifling N95s. Shockingly, there was a crowd of people by the lake. Most of them were not wearing face masks and they were barely practicing social distancing. We started to wonder why they behaved the way they did and how their behavior connected to the bigger picture in Canada. Thus, this analysis aims to address the question of how active people in Canada are, at practicing social distancing and the driving forces behind their social distancing decisions.


## Data Sources

- Google COVID-19 Community Mobility Reports https://www.google.com/covid19/mobility/
- Google Trends https://trends.google.com/trends/?geo=CA
- Canada COVID-19 Cases https://www.canada.ca/en/public-health/services/diseases/2019-novel-coronavirus-infection.html
- Government of Canada's Weather Data https://climate.weather.gc.ca/historical_data/search_historic_data_e.html
- Dates of Declaration of States of Emergency https://nationalpost.com/news/provincial-states-of-emergencies-were-issued-a-month-ago-most-are-coming-up-for-renewal


## Key metric

We created a new variable - social distancing score (`s_d_score`)
`s_d_score` = -1 * (`retail_recreation` + `grocery_pharmacy` + `parks` + `transit` + `workplaces`) + `residential`

The reason why we multiply -1 for the categories - `retail_recreation`, `grocery_pharmacy`, `parks`, `transit`, `workplaces` - is because we want to penalize the score when there is an increase in the number of visits of these places since these places are considered as public areas and a spike in the number of visits in these areas indicates that people are doing badly in social distancing in these areas. Whereas, people are encouraged to stay at home during COVID-19. Thus, we do not multiple `residential` by -1.


## Exploratory Data Analysis

To get a general sense of people’s behavior during COVID-19, we first took a look into the most and least frequent places people visited. Following measures taken in March to stop the spread of COVID-19, people stopped using public transportation and decreased their number of visits to workplaces. They stayed home most of the time with little variation from day to day. However, data showed that people visited parks quite often. There are numerous days where the number of visits to parks surged suddenly. Interestingly, Google trends show a similar pattern in which there is a strong correlation between the number of times people searched for “parks” and the number of times people visited parks.


## Modeling

We computed the permutation feature importance after fitting a random forests classifier to our data. The mean temperature, new cases, new deaths in Canada are the variables that have the most predictive power. On the other hand, days since the first case, new deaths, and new cases in the world have the least predictive power. To look into the individual effects of the factors, we fitted a multiple linear regression. Mean temperature and new cases in Canada remain significant, while new deaths become less significant. This indicates that as the weather gets warmer and as we enter summer, people want to go out more to bathe in the sun. People are also responsive to the number of new cases and they will act accordingly. Total precipitation is another significant factor. People may decide to stay at home if it is raining outside


## Conclusion

Canada's social distancing is responsive to new cases in Canada, temperature, and precipitation. As we are entering summer, it is our job to practice social distancing when going outside for a walk and the government should constantly remind people to take precautions during the pandemic.
