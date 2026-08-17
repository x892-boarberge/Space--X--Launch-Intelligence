# 02 – Data Sources & Variable Dictionary

## Project Goal
Investigate Falcon 9 capacity allocation pressure created by Starlink demand and the speed at which Starship can relieve that pressure.

## Primary Data Sources

### 1. Launch & Booster Data (Highest Priority)
- SpaceX API / community snapshots
- Launch Library 2 (The Space Devs)
- Jonathan McDowell’s launch logs
- Kaggle SpaceX launch datasets (starting point)

Key fields:
- flight_number
- date_utc
- booster_serial / core
- core flight number (reuse count)
- launch_success
- landing_success
- landing_type
- launchpad
- payloads (Starlink count and version)

### 2. Starlink Business Metrics
- SpaceX SEC filings
- Official Starlink status pages
- Industry reports (Reuters, CNBC, etc.)

Key fields:
- Subscribers
- ARPU
- Active satellite count
- Satellite generation mix

### 3. Starship Flight Log
- NASASpaceflight.com
- SpaceX official flight pages
- Wikipedia List of Starship launches

Key fields:
- Flight number
- Date
- Vehicle version (V1/V2/V3)
- Booster outcome
- Ship outcome
- Payload type
- Catch attempts

### 4. External Capacity Signals
- Reuters, SpaceNews, Ars Technica reporting
- Customer statements about launch availability

## Core Variables

| Variable              | Description                                      | Type        |
|-----------------------|--------------------------------------------------|-------------|
| booster_serial        | Unique booster identifier                        | string      |
| flight_number         | Number of flights this booster has flown         | integer     |
| mission_date          | Launch date                                      | date        |
| turnaround_days       | Days since previous flight of same booster       | integer     |
| mission_type          | Starlink / Commercial / NASA / Other             | categorical |
| satellites_deployed   | Number of Starlink satellites on that mission    | integer     |
| satellite_version     | V1 / V2 / V2 Mini / V3                           | categorical |
| landing_success       | Whether booster landed successfully              | boolean     |
| starlink_share        | % of Falcon 9 missions that were Starlink        | float       |
| subscribers           | Starlink subscriber count                        | integer     |
| arpu                  | Average revenue per user                         | float       |
| starship_flight_id    | Flight designation                               | string      |
| orbital_attempt       | Whether the flight targeted orbit                | boolean     |
| ship_catch_attempted  | Whether ship catch was attempted                 | boolean     |

## Derived Metrics
- Turnaround time by flight-number bins
- Monthly/quarterly Starlink share of Falcon 9 capacity
- Network capacity proxy per launch
- Starship success rate by mission phase