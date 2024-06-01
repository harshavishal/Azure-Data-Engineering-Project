# Azure-Data-Engineering-Project | Tokyo Olympics Data Analytics

This project demonstrates a comprehensive data engineering and analytics workflow using the Tokyo Olympic dataset. The process begins with ingesting a CSV file from GitHub into the Azure ecosystem via Azure Data Factory. The data is initially stored in Azure Data Lake Storage Gen2 and then transformed using Azure Databricks. The enriched data is subsequently stored back in ADLS Gen2. Advanced analytics are conducted in Azure Synapse, with final insights visualized in Azure Synapse or Power BI.

## Architecture

### Dataset Used
This dataset contains details of over 11,000 athletes, 47 disciplines, and 743 teams participating in the 2021 (2020) Tokyo Olympics. It includes information about athletes, coaches, teams, and entries by gender, with details like names, countries represented, discipline, and gender of competitors.

#### Source: [2021 Olympics in Tokyo](https://www.kaggle.com/datasets/arjunprasadsarkhel/2021-olympics-in-tokyo)

## Azure Services Used
1. **Azure Data Factory:** For data ingestion from GitHub.
2. **Azure Data Lake Storage Gen2:** As the primary data storage solution.
3. **Azure Databricks:** For data transformation tasks.
4. **Azure Synapse Analytics:** To perform in-depth data analytics.
5. **Power BI:** For data visualization.

## Workflow

### Initial Setup
1. **Create Azure Free Subscription Account**
2. **Resource Group:** Create a Resource Group `tokyo-olympic-data` to house and manage all the Azure resources associated with this project.
3. **Storage Account:** Set up a storage account in the resource group, configured to leverage Azure Data Lake Storage (ADLS) Gen2 capabilities.
4. **Container:** Create a container inside this storage account to hold the project's data. Two directories, `raw-data` and `transformed-data`, are created to store raw and transformed data, respectively.

### Data Ingestion using Azure Data Factory
1. Create an Azure Data Factory workspace within the resource group.
2. Launch the Azure Data Factory Studio.
3. Upload the Tokyo Olympics dataset from Kaggle to GitHub.
4. Initialize a new data integration pipeline in the studio.
5. Use the Copy Data task to move data efficiently between various sources and destinations.
6. Configure the Data Source with the HTTP template, as we are using an HTTP request to get the data from the GitHub repo.
7. Establish the Linked Service for the source.
8. Configure the File Format and set up the Linked Service Sink.
9. Repeat the above steps to load all datasets.
10. Run all the copy data activities at once.
11. Validate that the files like `athletes.csv`, `medals.csv`, etc., are present in the `raw-data` folder in Azure Data Lake Storage Gen2.

### Data Transformation using Azure Databricks
1. Navigate to Azure Databricks within the Azure portal, create a workspace within the resource group, and launch it.
2. Configure compute in Databricks.
3. Create a new notebook within Databricks and rename it appropriately.
4. Establish a connection to Azure Data Lake Storage (ADLS) using credentials (Client ID, Tenant ID, Secret).
5. Write code to mount ADLS Gen2 to Databricks.
6. Perform data transformations and write the transformed data back to ADLS Gen2.
7. Refer to the `Tokyo Olympics Transformation.ipynb` notebook for the transformations and code used to mount ADLS Gen2 to Databricks.

### Setting Up and Using Azure Synapse Analytics
1. Create a Synapse Analytics Workspace.
2. Within the Workspace, navigate to the "Data" section, choose "Lake Database", and create a Database `TokyoOlympicDB`.
3. Create tables from the transformed data folder within your ADLS Gen2 storage.

### Performing Data Analysis on the Data
1. Create SQL scripts to perform exploratory data analysis using SQL.
2. Use Power BI to generate analysis reports.
3. Refer to the `Tokyo Olympics SQL script.sql` for the SQL scripts used for data analysis.
