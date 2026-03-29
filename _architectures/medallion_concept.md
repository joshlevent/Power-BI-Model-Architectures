---
title: Medallion Concept Fabric Architecture
description: A Medallion Concept Fabric Architecture
layout: page
nav_order: 3
---

# Medallion Concept Fabric Architecture

![Medallion Concept  Fabric Architecture](medallion_concept.png)

This architecture makes sense for organisations that want to fully embrace Fabric as a data platform.

Here, IT is responsible for the data platform as a whole, and the ingestion and cleaning of data. Business Units are then responsible for additional transformations of data in preparation for analysis and visualisation in Power BI.

The Bronze Lakehouse is for storing data in a raw form, as it comes from the source.

The Silver Lakehouse stores all data in cleaned-up tables with standardised naming.

The Gold Data Warehouse stores transformed data that has been prepared for analytics.

Within the Report Workspace, most of the data transformations should take place in the Data Factory rather than the Power Query that generates the semantic model.

There are two reasons for this. The first is that this way, potentially reusable data is stored in the Gold Data Warehouse where it can be easily reused. The second is that this creates clarity about where analytic transformations take place.

There are many ways to prepare the transformations for the Data Warehouse (and the Lakehouses). I recommend sticking with PySpark Notebooks or Dataflows in workspaces managed by a Business Unit (IT-managed workspaces may wish to use SQL or other tools more suitable for data engineers).

Dataflows are based on Power Query, which Power BI developers will already be familiar with. This allows you to keep the number of different programming languages to a minimum. A PySpark Notebook is a good alternative for data scientists who are more familiar with Python.
