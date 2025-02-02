# Real Estate Data Pipeline Project

This project demonstrates an end-to-end data pipeline that processes real estate data from Redfin, stores it in AWS S3, transforms the data, and then ingests it into Snowflake for analysis in Power BI. The pipeline showcases modern data engineering practices for handling, transforming, and visualizing large datasets.

## Workflow Overview

1. **Data Extraction**: Retrieve real estate data from Redfin.
2. **Data Storage (Raw)**: Store the raw data in an AWS S3 bucket.
3. **Data Transformation**: Process and clean the data to make it analysis-ready.
4. **Data Storage (Transformed)**: Save the transformed data back into a different S3 bucket.
5. **Data Loading (Snowflake)**: Use Snowpipe to ingest the transformed data into Snowflake.
6. **Data Visualization**: Connect Power BI to Snowflake to create insightful visualizations.
---

## Images

### Workflow Diagram
![Workflow Diagram](https://github.com/Usama00004/ETL-Pipeline/blob/main/images/Image_1.png)

### Air Flow Dag
![Sample Dashboard](https://github.com/Usama00004/ETL-Pipeline/blob/main/images/Image_3.png)

### Executing Snow Pipe
![Sample Dashboard](https://github.com/Usama00004/ETL-Pipeline/blob/main/images/Image_4.png)
---

## Key Components

### 1. **Data Extraction**
- Source: Redfin real estate data.
- Tools: Python with libraries like `requests` or `selenium` (depending on data source).
- Output: CSV files.

### 2. **AWS S3 Buckets**
- **Raw Data Bucket**: Stores the unprocessed data.
- **Transformed Data Bucket**: Stores the cleaned and transformed data.

### 3. **Data Transformation**
- Tools: Python (Pandas, PySpark, etc.).
- Tasks:
  - Handle missing or inconsistent data.
  - Normalize or standardize fields.
  - Format data for Snowflake ingestion.

### 4. **Snowflake**
- **Snowpipe**: Automates data ingestion from the S3 transformed data bucket.
- **Schema Design**: Optimized for querying and analysis in Power BI.

### 5. **Power BI**
- Create dynamic dashboards to visualize real estate trends and insights.
- Connect directly to Snowflake for real-time data updates.

---

## Prerequisites

- **AWS S3**: Ensure access to an S3 bucket with necessary permissions.
- **Snowflake**: Active account and permissions to create Snowpipes and tables.
- **Power BI**: Installed on your local machine or accessed via Power BI Service.
- **Python**: Installed with required libraries (listed in `requirements.txt`).

---


## Setup Instructions

### 1. Clone the Repository
```bash
git clone <repository-url>
cd real-estate-pipeline
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Configure AWS and Snowflake
- Update the `config/aws_config.json` with your S3 bucket details.
- Update the `config/snowflake_config.json` with Snowflake connection parameters.

### 4. Run the Pipeline
- Extract data:
  ```bash
  python scripts/extract.py
  ```
- Upload raw data to S3:
  ```bash
  python scripts/load_to_s3.py --stage raw
  ```
- Transform data:
  ```bash
  python scripts/transform.py
  ```
- Upload transformed data to S3:
  ```bash
  python scripts/load_to_s3.py --stage transformed
  ```
- Ingest data into Snowflake:
  ```bash
  python scripts/load_to_snowflake.py
  ```

---

## Key Features

- **Automation**: Snowpipe automates data ingestion into Snowflake.
- **Scalable Storage**: AWS S3 ensures reliable and scalable storage for both raw and processed data.
- **Real-Time Analytics**: Power BI connects directly to Snowflake for real-time insights.
- **Custom Transformations**: Flexible transformation scripts ensure the data meets business needs.

---

## Future Enhancements

- Add CI/CD pipelines for automated deployment.
- Implement data validation and monitoring using tools like Great Expectations.
- Expand to support additional data sources beyond Redfin.
- Optimize Power BI dashboards for advanced analytics.



---

## License
This project is licensed under the MIT License. See the `LICENSE` file for more details.

---

## Contact
For questions or feedback, please contact [Usama Tahir](mailto:usamatahir00004@gmail.com).
