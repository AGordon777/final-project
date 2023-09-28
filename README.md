# National Food Balances

### Purpose

To investigate where food is produced and consumed; which countries are self-sufficient producers; how many kcal/day are available as food stocks in each country.


### Source data

https://www.fao.org/faostat/en/#data/ - three dataframes exported:
- NationalFoodBalancesByYear(2010-2020)
- NationalFoodBalancesHistoric(1961-2013)
- ProductionOutput - to be incorporated in PhaseII

https://ourworldindata.org/famines#famines-by-world-region-since-1860 - the table containing famine events was scraped

https://ourworldindata.org/grapher/national-gdp-constant-usd-wb - this generated the TARGET for the Regression model

https://ghoapi.azureedge.net/api/uwgt5 - retrieved via API but not used as incomplete


### Documentation

'data-cleaning-processing.ipynb' This file reformats the raw data from an extended pivot into narrower dataframes. It extracts useful features from within the column 'Element' and creates new columns for analysis.

'EDA.ipynb' This file further reformats and explores the datasets, enabling conclusions to be drawn. Dataframes from here are exported as .csv for visualisation in Tableau (link below). This file could certainly do with some restructuring!

'model.ipynb' This file contains a Regression model pipeline and optimisations to predict GDP/capita from food statistics.

'nutrition.ipynb' This briefly explored the WHO sourced data but found it to be incomplete and not usable for Phase 1.


### Summary

I reformatted both the historical and recent 'balance' datasets to find annual food holdings in kcal/capita/day. This can easily be compared to the World Food Organisation recommended average daily intake of 1,800 kcal as an indication of food availability.

I identified country-years affected by large recorded famines between 1961 and 2010 and found food balances for those datapoints.

I used the more recent dataset (2010-2020) to categorise countries into producers/importers/exporters relative to their population food requirements.

I tested various Regression models to predict GDP/capita. DecisionTreeRegressor with some parameter optimisations yielded a r2-score of over 0.90.


### Conclusions drawn

Few countries after 1980 have ever dropped below an annual national food balance of 1,800 kcal/capita/day even in famine years. This suggests that famines may be intra-national logistical or political constructs rather than simply due to the absolute availability of food in a country.

National stories can be seen in the food availability data. For example, rapid growth in China, Egypt and later Djibouti and catastrophic declines in Afghanistan since 1960.

GDP per capita in a given year can be predicted with good accuracy using features such as kcal/capita/day, fraction of kcal derived from animals vs plants, ratio of imported kcal to available kcal, protein g/capita/day, and population.


### Further investigation

This project scratched the surface of the information within the dataset.

Follow up ideas are:
- predicting health indicators with the same methodology
- investigating land use and yield efficiency
- determining if change in climate can be seen in the global distribution of crops produced
- investigating provenance / credibility of individual datapoints by country


### Data visualisation

https://public.tableau.com/app/profile/alexander.gordon5057/viz/foodproject_16958982754250/GlobalFoodBalances

