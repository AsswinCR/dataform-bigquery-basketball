# NCAA Basketball Data Analysis with Dataform

## Project Overview
This project implements a data transformation pipeline using Google Cloud Dataform to analyze NCAA Basketball data. We transform raw basketball data from BigQuery public datasets into analytical views for team and game performance analysis.

## Setup Steps

1. **Initial Configuration**
   - Created a new Dataform workspace "bb-workspace"
   - Updated workflow_settings.yaml:
   ```yaml
   defaultDatabase: "bigquery-public-data"
   defaultSchema: "ncaa_basketball"
   defaultLocation: "US"
   assertionSchema: "dataform_assertions"
   ```

2. **Source Declarations (sources.js)**
   ```javascript
   // Declared source tables from NCAA basketball dataset
   declare({
     name: "mbb_teams",
     database: "bigquery-public-data",
     schema: "ncaa_basketball",
     table: "mbb_teams"
   });
   // Similar declarations for:
   // - mbb_games_sr
   // - mbb_historical_teams_games
   // - mbb_historical_tournament_games
   // - mbb_players_games_sr
   ```

3. **Core Tables Created**
   - `dim_teams.sqlx`: Team dimension table
   - `dim_seasons.sqlx`: Season dimension table
   - `fact_games.sqlx`: Game facts table

4. **Analytical Views**
   - `view_team_scoring_leaders.sqlx`: Analysis of team scoring performance
     - Shows average points per game
     - Ranks teams by scoring within each season
     - Includes total points and games played

   - `view_team_win_loss_record.sqlx`: Team win/loss analysis
     - Calculates wins, losses, and win percentage
     - Provides ranking based on win percentage
     - Shows performance across seasons

   - `view_home_away_performance.sqlx`: Home vs Away analysis
     - Compares home and away game performance
     - Includes scoring differentials
     - Shows win percentages for both home and away games

## Project Structure
```
bb-workspace/
├── definitions/
│   ├── sources.js
│   ├── dim_teams.sqlx
│   ├── dim_seasons.sqlx
│   ├── fact_games.sqlx
│   ├── view_team_scoring_leaders.sqlx
│   ├── view_team_win_loss_record.sqlx
│   └── view_home_away_performance.sqlx
└── workflow_settings.yaml
```

## Key Features
- Star schema design for efficient querying
- Incremental processing where applicable
- Performance optimizations (filtering recent seasons, minimum game thresholds)
- Comprehensive team performance metrics

## Analytical Capabilities
1. **Team Performance Analysis**
   - Scoring leaders by season
   - Win-loss records
   - Home vs Away performance comparisons

2. **Data Quality**
   - Minimum game thresholds to ensure statistical significance
   - Proper handling of null values
   - Consistent data types (using CAST for numerical operations)

## Usage
1. Clone the repository
2. Configure Dataform workspace settings
3. Run the transformations in order:
   - First: Dimension tables (dim_*.sqlx)
   - Second: Fact tables (fact_*.sqlx)
   - Finally: Analytical views (view_*.sqlx)

## Future Enhancements
- Add player statistics analysis
- Include tournament performance metrics
- Implement season-over-season comparisons
- Add data quality tests

##### Disclaimer ⚠️ : This project was created as part of my learning process. While it's functional, there's significant room for improvement. I encourage experienced developers to contribute, suggest changes, or use this as a base to demonstrate better implementations.

