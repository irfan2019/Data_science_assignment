# Project Structure

```
Deutschlandticket_Assessment/
│
├── data/
│   ├── Bronze/
│   │   ├── Employees_table.csv
│   │   ├── Possible_generated_stations.csv
|    |    ├── Possible_generated_stations_new.csv
│   │   └── stops.txt
│   │
│   ├── Silver/
│   │   └── FE_cleaned_table.csv
│   │
│   └── Gold/
│       ├── Gold_Employees.csv
│       └── Gold_Area_Summary.csv
│
├── notebooks/
│   ├── 01_Data_Generation.ipynb
│   ├── 02_Processed.ipynb
│   ├── 03_Analysis.ipynb
│   └── 04_Visualization.ipynb
│
├── requirements.txt
└── README.md
```

---

# Synthetic Employee Generation


Since real employee addresses cannot be used, a synthetic employee dataset was created to simulate employees commuting to the Johnson & Johnson Medical GmbH office in Norderstedt.

Approximately **800 synthetic employees** were generated across **50 residential locations** covering Hamburg and surrounding municipalities such as Norderstedt, Pinneberg, Quickborn, Wedel, Elmshorn, Ahrensburg, Bergedorf and Lüneburg.

Each residential location were assigned to predefined share The shares sum to **1.0**, ensuring all employees were proportionally distributed.

For every employee:

- A residential area was selected with predefined population share.
- Random latitude and longitude noise were generated around the area coordinates.
- A fixed random seed (`random.seed(42)` and `numpy.random.seed(42)`) was used to multiply.

# Business Analysis


## Areas with Strong Public Transport Connectivity

The top 5 places with strong Public transport connectivity :

- Fuhlsbüttel
- Bramfeld
- Alsterdorf
- Hamburg-Nord
- Wellingsbüttel

| Location | Avg. Commute Time (min) | Unique Stations | Main Station | Connectivity Category |
|----------|-------------------------:|----------------:|--------------|-----------------------|
| Fuhlsbüttel | 38.12 | 4 | Langenhorn Markt | Strong public transport connectivity |
| Bramfeld | 44.52 | 5 | Barmbek | Strong public transport connectivity |
| Alsterdorf | 44.26 | 7 | U Alsterdorf | Strong public transport connectivity |
| Hamburg-Nord | 49.38 | 12 | U Lattenkamp | Strong public transport connectivity |
| Wellingsbüttel | 42.46 | 5 | Airport (Flughafen) | Strong public transport connectivity |

## Why Are These Areas Well Connected?

- Average commute times below **45 minutes**
- Short walking distances to the nearest HVV station

## Areas with Less Attractive Public Transport

The top 5 places with weak Public transport connectivity :

- Lüneburg
- Itzehoe
- Seevetal
- Bad Oldesloe
- Buxtehude



| Location | Avg. Commute Time (min) | Unique Stations | Main Station | Connectivity Category |
|----------|-------------------------:|----------------:|--------------|-----------------------|
| Lüneburg | 128.11 | 1 | Lüneburg | Less attractive public transport |
| Itzehoe | 106.74 | 1 | Elmshorn | Less attractive public transport |
| Seevetal | 88.12 | 1 | Maschen | Less attractive public transport |
| Bad Oldesloe | 81.32 | 1 | Bf. Bad Oldesloe (ZOB) | Less attractive public transport |
| Buxtehude | 81.22 | 1 | Buxtehude ZOB | Less attractive public transport |


## Why Are These Areas poorly connected?

- Longer commute times beyond (**1 hour**)
- Few stations nearby
- the adoption rate for Deutschand ticket is very minimal



## Key Factors Influencing Deutschlandticket Adoption

The rule-based assessment shows we can identify various sectors.

### Commute Time

Employees with commute time below **45 minutes** are classified as **Very High**, Shows the adoption for deustchland ticket rate is very high and helpful

| Commute Time | Employees | Percentage (%) |
|--------------|----------:|---------------:|
| Within 30 minutes | 20 | 2.55 |
| Within 45 minutes | 219 | 27.97 |
| Within 60 minutes | 596 | 76.12 |
| Over 60 minutes | 187 | 23.88 |


| Deutschlandticket Metric | Employees | Percentage (%) |
|---------------------------|----------:|---------------:|
| Very High | 540 | 68.97 |
| High | 149 | 19.03 |
| Low | 83 | 10.60 |
| Very Low | 11 | 1.40 |


### Distance to the Office

Employees living with short distance to the office prefer walking directly to the office. Similarly people near to the office can commute via bike (less than kms)

### Station Accessibility

Residential areas and cities are well connected to the nearby stations with multiple statiosn accessibility achieveing a higher connectivity score

