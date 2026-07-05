# Daikibo Factory Machine Downtime Analysis | Tableau Dashboard

## Project Overview

This project analyzes machine telemetry data collected from four Daikibo manufacturing factories during **May 2021**. The objective is to identify which factory experienced the most machine downtime and determine which machine types contributed most to the downtime.

The analysis was completed using **Tableau**, where calculated fields, interactive visualizations, and dashboards were developed to transform raw telemetry data into actionable business insights.

---

## Business Problem

Daikibo collected telemetry data from its manufacturing facilities to answer the following business questions:

1. Which factory experienced the highest amount of machine downtime?
2. Which machine types contributed the most downtime in that factory?

Understanding these patterns helps maintenance teams prioritize inspections, improve equipment reliability, and reduce production losses.

---

## Dataset Information

The dataset contains telemetry messages collected every **10 minutes** from machines operating in four factories.

### Factory Locations

* Daikibo Factory Meiyo (Tokyo, Japan)
* Daikibo Factory Seiko (Osaka, Japan)
* Daikibo Berlin (Berlin, Germany)
* Daikibo Shenzhen (Shenzhen, China)

### Dataset Characteristics

* Data Format: JSON
* Time Period: May 2021
* Telemetry Frequency: Every 10 minutes
* Number of Factory Locations: 4
* Number of Machine Types: 9

Each telemetry record includes machine information such as:

* Factory
* Device Type
* Machine Status
* Timestamp

---

## Objective

The primary objective of this project is to analyze unhealthy machine events and calculate the potential machine downtime across factories.

Each unhealthy machine status represents **10 minutes of downtime**, based on the telemetry collection interval.

---

## Tools Used

* Tableau Desktop
* JSON Dataset
* GitHub

---

## Data Preparation

A calculated field named **Unhealthy** was created to calculate downtime.

### Calculated Field

```tableau
IF [Status] = "unhealthy" THEN 10
ELSE 0
END
```

This assigns:

* 10 minutes for every unhealthy status
* 0 minutes for every healthy status

The calculated field is then aggregated using `SUM(Unhealthy)` to determine total downtime.

---

## Dashboard Components

### 1. Down Time per Factory

Visualization Type:

* Horizontal Bar Chart

Purpose:

* Displays the total downtime for each factory.
* Helps identify which factory experienced the highest machine downtime.

Measures Used:

* SUM(Unhealthy)

Dimension:

* Factory

---

### 2. Down Time per Device Type

Visualization Type:

* Horizontal Bar Chart

Purpose:

* Displays downtime by machine type.
* Used to determine which equipment generated the highest downtime.

Measures Used:

* SUM(Unhealthy)

Dimension:

* Device Type

---

### 3. Interactive Dashboard

The dashboard combines both visualizations into a single interactive interface.

Interaction:

* Selecting a factory in the first chart filters the second chart.
* The second chart immediately displays downtime only for the selected factory.

This allows users to drill down from factory-level performance to machine-level performance.

---

## Dashboard Features

* Interactive filtering
* Dynamic machine analysis
* Factory-wise comparison
* Device-wise comparison
* Clean and simple layout
* Easy business interpretation

---

## Key Insights

The dashboard helps answer the following questions:

* Which factory recorded the most downtime?
* Which device type failed most frequently?
* How does downtime vary across factories?
* Which machines require preventive maintenance?
* Which factory should be prioritized for operational improvements?

---

## Project Workflow

1. Import JSON telemetry dataset into Tableau.
2. Review and verify data fields.
3. Create the calculated field `Unhealthy`.
4. Build the **Down Time per Factory** bar chart.
5. Build the **Down Time per Device Type** bar chart.
6. Create an interactive dashboard.
7. Configure the first chart as a filter.
8. Validate dashboard interactions.
9. Publish the project to GitHub.

---

## Repository Structure

```text
Daikibo-Factory-Downtime/
│
│
├── Dashboard/
│   └── Daikibo_Dashboard.twbx
│
├── Images/
│   └── Dashboard.png
│
├── README.md
│
└── daikibo_telemetry.json
```

---

## Dashboard Preview

Add a screenshot of your Tableau dashboard in the `Images` folder and display it here.

```markdown
![Dashboard](Images/%7B31118191-2527-46E4-959D-04CE23096004%7D.png)
```

---

## Future Improvements

Possible enhancements include:

* Monthly trend analysis
* Daily downtime monitoring
* Predictive maintenance dashboards
* Machine health score
* Factory performance KPIs
* Maintenance scheduling analytics

---

## Learning Outcomes

Through this project, the following Tableau concepts were applied:

* Calculated Fields
* Aggregations
* Interactive Dashboards
* Dashboard Actions
* Filtering
* Bar Charts
* Data Visualization Best Practices
* Business Intelligence Reporting

---

## Conclusion

This Tableau dashboard provides a simple and interactive way to analyze machine downtime across Daikibo factories. By identifying the factory with the highest downtime and the device types contributing most to failures, stakeholders can make informed maintenance and operational decisions that improve equipment reliability and manufacturing efficiency.
