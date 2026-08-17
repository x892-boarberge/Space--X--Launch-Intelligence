# 03 – Data Dictionary

This document defines all key variables used in the SpaceX Launch Capacity & Starship Transition Intelligence project.

## 1. Falcon 9 & Booster Variables

| Variable              | Description                                              | Data Type   | Example                  | Source                  |
|-----------------------|----------------------------------------------------------|-------------|--------------------------|-------------------------|
| booster_serial        | Unique identifier of the Falcon 9 booster                | string      | B1062                    | SpaceX / Launch Library |
| flight_number         | Number of times this booster has flown                   | integer     | 27                       | SpaceX                  |
| mission_date          | Date of the launch                                       | datetime    | 2026-06-15               | SpaceX / Launch Library |
| previous_mission_date | Date of the previous flight of the same booster          | datetime    | 2026-04-28               | Calculated              |
| turnaround_days       | Number of days between consecutive flights               | integer     | 48                       | Calculated              |
| mission_name          | Official name of the mission                             | string      | Starlink Group 10-12     | SpaceX                  |
| mission_type          | Category of the mission                                  | categorical | Starlink / Commercial / NASA / Other | Derived     |
| launch_site           | Launch site used                                         | string      | CCSFS SLC-40             | SpaceX                  |
| landing_success       | Whether the booster successfully landed                  | boolean     | True                     | SpaceX                  |
| landing_type          | Type of landing attempted                                | categorical | ASDS / RTLS / Ocean / None | SpaceX               |
| satellites_deployed   | Number of Starlink satellites deployed on the mission    | integer     | 29                       | SpaceX                  |
| satellite_version     | Generation of Starlink satellites deployed               | categorical | V1 / V2 / V2 Mini / V3   | SpaceX / Reports        |

## 2. Starlink Business Variables

| Variable              | Description                                              | Data Type   | Example     | Source              |
|-----------------------|----------------------------------------------------------|-------------|-------------|---------------------|
| report_date           | Date of the metric                                       | datetime    | 2026-03-31  | SEC / Reports       |
| subscribers           | Total number of Starlink subscribers                     | integer     | 10300000    | SEC filings         |
| arpu                  | Average Revenue Per User (monthly)                       | float       | 66.0        | SEC filings         |
| active_satellites     | Number of active Starlink satellites in orbit            | integer     | 9600        | SpaceX / Reports    |
| satellites_launched   | Number of satellites launched in the period              | integer     | 450         | Calculated          |

## 3. Starship Variables

| Variable                  | Description                                          | Data Type   | Example          | Source                  |
|---------------------------|------------------------------------------------------|-------------|------------------|-------------------------|
| starship_flight_id        | Flight designation                                   | string      | Flight 13        | SpaceX / NSF            |
| flight_date               | Date of the Starship flight                          | datetime    | 2026-07-24       | SpaceX                  |
| vehicle_version           | Version of Starship / Super Heavy                    | categorical | V1 / V2 / V3     | SpaceX / NSF            |
| booster_outcome           | Result of the booster recovery                       | categorical | Caught / Soft Splash / Hard Splash / Lost | NSF / SpaceX |
| ship_outcome              | Result of the ship recovery / landing                | categorical | Intact Splash / Destroyed / Caught | NSF / SpaceX |
| orbital_attempt           | Whether the flight targeted orbit                    | boolean     | False            | SpaceX / NSF            |
| ship_catch_attempted      | Whether a tower catch of the ship was attempted      | boolean     | False            | SpaceX / NSF            |
| payload_type              | Type of payload carried                              | string      | Starlink V3      | SpaceX                  |
| payload_success           | Whether the payload was successfully deployed        | boolean     | True             | SpaceX                  |

## 4. Derived / Calculated Metrics

| Metric                        | Description                                              | Calculation Method                              |
|-------------------------------|----------------------------------------------------------|-------------------------------------------------|
| starlink_share                | Percentage of Falcon 9 missions used by Starlink         | Starlink missions / Total Falcon 9 missions     |
| avg_turnaround_by_bin         | Average turnaround days by reuse count range             | Grouped by flight_number bins                   |
| capacity_per_launch           | Proxy for network capacity delivered per launch          | satellites_deployed × version capacity factor   |
| external_capacity_indicator   | Qualitative or quantitative signal of available capacity | Based on reports + residual missions            |