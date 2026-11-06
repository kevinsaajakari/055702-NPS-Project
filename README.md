# 055702-NPS-Project

Group project for Nonparametric Statistics course, including data, code, and analysis to identify congestion patterns in Paris transportation network.

## Introduction

### Context

The Paris Region (Île-de-France) has the most extensive public transportation network in Europe. It is composed of many transport modes: bus, tram, tram-train, cable car, bus-boat, light metro, metro, commuter rail and train. Île-de-France Mobilité (IDFM) is the managing authority of the network used daily by approximately ten million commuters. [1]

Before boarding in, rail transport means (tram-train, light metro, metro, commuter rail and train) require travellers to enter a station, validate their ticket and wait on a platform. In a mass transit context, knowledge on transportation patterns can help mobility service providers improve service quality and security. More precisely, knowing how many commuters enter a station at a given time of the day can help efficiently allocating resources for monitoring and regulating within-station traffic, such as coordinating agents able to anticipate peaks of arrivals. It is nonetheless important to compare the rate of arrivals of passengers at a station with its capacity. If the platform is congested, it becomes hard for travellers to exit the station which worsens the situation even more. It results in an increase of the usual overcrowding hazard on top of which we can add risks of falling on the track.

### Data 

Our data is the average hourly distribution of entry validations over different day types and for each station of the IDMF rail network, averaged over the second semester of 2026. [2] We were able to retrieve 763 stations. The day categories are:

- WD: Working day (outside of school holidays periods)

- WDSH: Working day during school holidays

- SA: Saturday (outside of school holidays periods)

- SASH: Saturday during school holidays

- SUPH: Sunday and bank holidays

Given station $s \in S$, day type $d \in D$ and $t \in \{0,\dots,23\}$, the relative number of validations in the time period $[t:00,t+1:00[$ is $x_t^{s,d} \in [0,100]$, given as a percentage. Consequently, our data is said to be *compositional*: $$\forall s \in S, \forall d \in D, \sum_{t=0}^{23} x_t^{s,d}=100$$

### Research Question

Supposing that

- The relative number of validations is representative of the relative number of travellers entering a station

- The daily number of users of a station is representative of its capacity

We believe that our data set is suitable to answer the following research question:

> How to identify patterns in the use of rail stations in an actionable manner to improve quality of service and security?

### Tentative Workflow

After eventually applying the Centred Log Ratio transform:

1.  Functional nonparametric biclustering using `FunCC`

2.  Investigating biclusters using depth measure and their differences using permutational inference

3.  Comparing results with data from another year or another semester

4.  Regression over local station parameters (e.g.: number of people working or living close) using nonparametric regression and prediction for a new station using conformal prediction

### Sources

[1] [IDFM's Website](https://www.iledefrance-mobilites.fr/decouvrir/nos-missions){.uri}

[2] [IDFM Open Data](https://data.iledefrance-mobilites.fr/explore/dataset/validations-reseau-ferre-profils-horaires-par-jour-type-2eme-trimestre/table/?sort=-code_stif_arret)
