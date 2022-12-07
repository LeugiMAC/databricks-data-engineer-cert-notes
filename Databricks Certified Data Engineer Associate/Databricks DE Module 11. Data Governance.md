#databricks #dataengineering 

[Databricks Certified Data Engineer Associate](Databricks%20Certified%20Data%20Engineer%20Associate.md)


## Key Functional Areas

- ### Data Access Control
| Who can access which data

- ### Data Access Audit
Capture and record all access to data 

- ### Data Lineage 
Capture upstream sources and downstream consumers

- ### Data Discovery
Ability to search for and discover authorised assets

---

## Unity Catalog

The Unity Catalog exists at an Account Level, allowing users to work on multiple workspaces.

Databricks allows you to configure permissions for the following objects: 

- Catalog
- Database
- Table
- View
- Function
- Any File

`Note: Files can be accessed outside of the Unity Catalog if permission have been granted at that level`

### Granting Privileges

- Databricks administrator: can grant access to all objects in the catalog and the underlying file system
- Catalog owner: All objects in the catalog
- Database owner: All objects in the database
- Table owner: Only the table


### Privileges

- ALL PRIVILEGES
- SELECT
- MODIFY
- READ_METADATA: Ability to view an object and its metadata
- USAGE: does not give any abilities, but is an additional requirement to perform any action on a database object. 
- CREATE

