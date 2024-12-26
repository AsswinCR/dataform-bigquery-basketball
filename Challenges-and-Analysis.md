# Challenges and ways to solve this assignment in NCAA Basketball Data Analysis Project

## Data Structure Challenges
1. **Schema Mismatches**
   - Initially assumed wrong column names (game_id, opponent_id)
   - Solution: Had to examine actual table schema using test queries
   - Learned to verify field names before writing complex transformations

2. **Project Configuration Issues**
   - Encountered "Dataset not found" errors due to incorrect project settings
   - Original error: "Not found: Dataset rapsodo-basketball-444807:dataform"
   - Solution: Updated workflow_settings.yaml with correct BigQuery public dataset paths

3. **Data Type Handling**
   - Faced issues with numeric comparisons (INT64 vs STRING)
   - Error: "No matching signature for operator >= for argument types: INT64, STRING"
   - Solution: Properly cast values and use consistent data types (FLOAT64 for points)

4. **Join Complexities**
   - Had to restructure queries due to home/away team data being in separate columns
   - Challenge in combining home and away statistics
   - Solution: Used UNION ALL to combine both perspectives of games

## Technical Hurdles
1. **Database Access**
   - Initial access issues with BigQuery public datasets
   - Solution: Corrected database and schema references in source declarations

2. **Query Performance**
   - Large dataset processing challenges
   - Solution: Added filters for recent seasons (>= 2015) and minimum game thresholds

3. **View Dependencies**
   - Managing the correct order of table and view creation
   - Solution: Implemented proper ref() references and dependency management

## Development Process Learnings
1. **Incremental Development**
   - Started with basic tables before complex views( to get an idea of how hte table looks)
   - Tested each component separately before integration
   - Used iterative approach to build and verify functionality

2. **Error Handling Strategy**
   - Developed testing small chunks of SQL before full implementation
   - Used test queries to verify results
  

3. **Best Practices Developed**
   - Always verify schema before writing transformations
   - Test queries with small data samples first
   - Use consistent naming conventions
   - Document changes and reasons for modifications

