# Daikibo Project: Telemetry & Compensation Data Analysis

This project presents an analysis of two distinct datasets from the company **Daikibo**: machine telemetry data and employee compensation information. The goal is to provide actionable insights into operational efficiency and internal pay equity using a combination of **Tableau** and **Microsoft Excel**.

---

## 1. Machine Telemetry Analysis (Tableau)

This section focuses on identifying and visualizing potential machine downtime. The analysis is built on telemetry data from various factories and device types.

<img width="640" height="793" alt="image" src="https://github.com/user-attachments/assets/f53f6b5c-d509-44c5-b805-e14a7983980b" />


### 1.1 Project Objectives

- Analyze machine status data to quantify downtime.
- Create interactive visualizations to identify downtime trends by factory and device type.
- Build a dashboard that allows users to drill down into the data to pinpoint the most problematic areas.

### 1.2 Prerequisites

- **Software**: Tableau Desktop (A free trial is available)
- **Data**: `daikibo-telemetry-data.json`

### 1.3 Analysis Workflow

**Data Ingestion**  
Import the `daikibo-telemetry-data.json` file into Tableau.

**Metric Calculation**  
Create a new calculated field named `Unhealthy`. This field assigns a value of `10` (representing 10 minutes of potential downtime) for every record where the device status is `"unhealthy"`.

**Visualization Generation**

- **Bar Chart 1**: Visualize total "Unhealthy" time aggregated by Factory.
- **Bar Chart 2**: Visualize total "Unhealthy" time aggregated by Device Type.

**Dashboard Creation**

- Combine both charts into a single interactive dashboard.
- Set the "Down Time per Factory" chart to function as a filter. Clicking on a specific factory's bar will automatically update the second chart to show only the device types within that selected factory.

### 1.4 Result

The interactive dashboard highlights the factory with the highest total downtime, providing a clear starting point for maintenance and operational teams to investigate.

 A live version of the visualization is available on Tableau Public: **Tableau Public Link**

---

## 2. Employee Compensation Analysis (Excel)

This part of the project classifies employee compensation scores to evaluate the fairness of pay across the organization.

### 2.1 Prerequisites

- **Software**: Microsoft Excel or any compatible spreadsheet application
- **Data**: `Equality Table.xlsx` → `Sheet1.csv`

### 2.2 Analysis Workflow

**Data Access**  
The provided CSV file contains three key data points per employee:  
- Factory  
- Job Role  
- Equality Score (an integer between −100 and +100, where a score of 0 indicates perfect equality)

**Classification**  
A new column, `Equality Class`, was added to categorize each employee's score based on the following rules:

- **Fair**: Score between −10 and +10  
- **Unfair**: Score between −20 and −11 OR between +11 and +20  
- **Highly Discriminative**: Score less than −20 OR greater than +20

### 2.3 Excel Formula

The following formula was used in cell `D2` and applied to the rest of the column to perform the classification automatically:

```excel
=IF(AND(C2>=-10, C2<=10), "Fair", IF(OR(C2<-20, C2>20), "Highly Discriminative", "Unfair"))
```

---

## Repository Structure

```
├── daikibo-telemetry-data.json
├── Equality Table.xlsx
└── README.md
```

---

## Notes

- Ensure Tableau Desktop is installed before attempting the telemetry analysis.
- The Excel formula can be adapted for other datasets with similar scoring systems.
- For best results, keep data formats consistent and validate inputs before analysis.

---
