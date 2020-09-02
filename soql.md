## SOQL

* 100 soql queries per transaction
    * Double in Async.
    * Aggregate queries are 3 times the SOQL query limit(Includes subqueries)
* 50,000 query rows
* 50 mill. in batch (with query locator)
    ```sql
    SELECT [fieldList], [subquery] 
    TYPEOF <typeOfField> when <expression> else <expression> END
    FROM [sObjectType]
    USING SCOPE [filterScope]
    ```

### Type Of 
* Used when dealing with polymorphic fields (ownerId, whatId)
    ```sql
    SELECT 
      TYPEOF What
        WHEN Account THEN Phone, NumberOfEmployees
        WHEN Opportunity THEN Amount, CloseDate
        ELSE Name, Email
      END
    FROM Event
    ```

### Using Scope    
Available Scopes : everything, mine, mine_and_my_groups, my_territory, my_team_territory, team

    ```sql
    SELECT Id, CaseNumber
    FROM CASE
    USING SCOPE MINE
    ```