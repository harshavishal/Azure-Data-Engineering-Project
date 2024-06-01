# Azure-Data-Engineering-Project | Tokyo Olympics Data Analytics
This project provides a data engineering and analytical journey on the Tokyo Olympic dataset. It showcases how to ingest, transform, analyze, and visualize data using various Azure services. Starting with a CSV on GitHub, the data is ingested into the Azure ecosystem via Azure Data Factory, initially stored in Azure Data Lake Storage Gen2, then transformed in Azure Databricks. The enriched data, once again housed in ADLS Gen2, undergoes advanced analytics in Azure Synapse, and the insights are finally visualized in Azure Synapse or Power BI.

## Architecture
Dataset Used
This dataset contains details of over 11,000 athletes, 47 disciplines, and 743 teams participating in the 2021 (2020) Tokyo Olympics. It includes information about athletes, coaches, teams, and entries by gender, with details like names, countries represented, discipline, and gender of competitors.

Source: [2021 Olympics in Tokyo](https://www.kaggle.com/datasets/arjunprasadsarkhel/2021-olympics-in-tokyo)

Azure Services Used
Azure Data Factory: For data ingestion from GitHub.
Azure Data Lake Storage Gen2: As the primary data storage solution.
Azure Databricks: For data transformation tasks.
Azure Synapse Analytics: To perform in-depth data analytics.
Power BI: For data visualization.
Workflow
Initial Setup
Create Azure Free Subscription Account
Resource Group: Create a Resource Group tokyo-olympic-data to house and manage all the Azure resources associated with this project.
Storage Account: Set up a storage account in the resource group, configured to leverage Azure Data Lake Storage (ADLS) Gen2 capabilities.
Container: Create a container inside this storage account to hold the project's data. Two directories, raw-data and transformed-data, are created to store raw and transformed data, respectively.
Data Ingestion using Azure Data Factory
Create an Azure Data Factory workspace within the resource group.
Launch the Azure Data Factory Studio.
Upload the Tokyo Olympics dataset from Kaggle to GitHub.
Initialize a new data integration pipeline in the studio.
Use the Copy Data task to move data efficiently between various sources and destinations.
Configure the Data Source with the HTTP template, as we are using an HTTP request to get the data from the GitHub repo.
Establish the Linked Service for the source.
Configure the File Format and set up the Linked Service Sink.
Repeat the above steps to load all datasets.
Run all the copy data activities at once.
Validate that the files like "athletes.csv", "medals.csv", etc., are present in the "raw-data" folder in Azure Data Lake Storage Gen2.
Data Transformation using Azure Databricks
Navigate to Azure Databricks within the Azure portal, create a workspace within the resource group, and launch it.
Configure compute in Databricks.
Create a new notebook within Databricks and rename it appropriately.
Establish a connection to Azure Data Lake Storage (ADLS) using credentials (Client ID, Tenant ID, Secret).
Write code to mount ADLS Gen2 to Databricks.
Perform data transformations and write the transformed data back to ADLS Gen2.
Refer to the Tokyo Olympics Transformation.ipynb notebook for the transformations and code used to mount ADLS Gen2 to Databricks.
Setting Up and Using Azure Synapse Analytics
Create a Synapse Analytics Workspace.
Within the Workspace, navigate to the "Data" section, choose "Lake Database", and create a Database TokyoOlympicDB.
Create tables from the transformed data folder within your ADLS Gen2 storage.
Performing Data Analysis on the Data
Create SQL scripts to perform exploratory data analysis using SQL.
Use Power BI to generate analysis reports.
Refer to the Tokyo Olympics SQL script.sql for the SQL scripts used for data analysis.
