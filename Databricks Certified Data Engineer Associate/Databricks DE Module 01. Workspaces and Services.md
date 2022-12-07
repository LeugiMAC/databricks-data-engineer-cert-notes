#databricks #dataengineering 

[Databricks Certified Data Engineer Associate](Databricks%20Certified%20Data%20Engineer%20Associate.md)

## Architecture

![](../../../media/databricks_architecture_20221124135315.png)

## Databricks services in the Web Application

-   SQL
-   Machine Learning
-   Data Science and Engineering (Workspace)
-
## Clusters

- A set of one or more VM instances
- Driver: Coordinates activities of executors: Run tasks composing a Spark Job

![](../../../media/databricks_clusters_20221124135417.png)

### Types of clusters:

All-purpose Clusters:

-   Analyze data collaboratively using interactive notebooks
-   Create clusters from the workspace or API
-   Retains up to 70 clusters for up to 30 days

Job Clusters:

-   Run automated jobs
-   The Databricks job schedules creates job clusters when running jobs
-   Retains up to 30 clusters

## Repos

![](../../../media/ci_cd_workflows_with_git_20221129143828.png)

Example:
1.  Develop individual features in a feature branch and test using unit tests (e.g., implemented notebooks).
2.  Push changes to the feature branch, where the CI/CD pipeline will run the integration test.
3.  CI/CD pipelines on Azure DevOps can trigger Databricks Repos API to update this test project to the latest version.
4.  CI/CD pipelines trigger the integration test job via the Jobs API. Integration tests can be implemented as a simple notebook that will at first run the pipelines that we would like to test with test configurations. This can be done by just running an appropriate notebook with executing corresponding modules or by triggering the real job using [jobs API](https://docs.databricks.com/dev-tools/api/latest/jobs.html)
5.  Examine the results to mark the whole test run as green or red.


![](../../../media/ci_cd_best_practices_20221125143105.png)

### Collaborative Notebooks

- **Work together**: Real-time coauthoring, commenting and automated versioning simplify collaboration while providing control
- **Share insights**: Built-in interactive visualisations
- **Operationalize at Scale**: 
	- Schedule notebooks to automatically run. 
	- Create multi-stage pipelines using Notebooks workflows. 
	- Set up alerts and quick access audit logs for easy monitoring and troubleshooting