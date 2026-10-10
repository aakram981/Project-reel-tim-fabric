
<div align="center">

# 🚲 Real-Time Analytics with Microsoft Fabric
### Bike-Sharing Streaming Pipeline: Eventstream → Eventhouse → Live Dashboard

![Microsoft Fabric](https://img.shields.io/badge/Microsoft-Fabric-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Real-Time Intelligence](https://img.shields.io/badge/Real--Time-Intelligence-00A36C?style=for-the-badge)
![KQL](https://img.shields.io/badge/Language-KQL-5C2D91?style=for-the-badge)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)

</div>

---

## 📌 Project Overview

This project demonstrates an **end-to-end Real-Time Intelligence solution** built in Microsoft Fabric:

1. ⚡ **Ingest** streaming bike-sharing events with an **Eventstream**
2. 🔄 **Transform** the data on the fly (tumbling window, sum of bikes per street)
3. 🗄️ **Store** raw and aggregated data in an **Eventhouse** (KQL database)
4. 📊 **Visualize** live station activity in a **Real-Time Dashboard**

---

## 🏗️ Architecture

```text
 🚲 Bicycles (Source)
        │
        ▼
 🌊 Bicycle_Data-stream
        │
        ├──────────────► 🏠 Eventhouse   (raw events)
        │
        └─► ⚙️ GroupBystreet ─► 🏠 Eventhouse1 (aggregated per street)
            (Tumbling window · Sum of No_Bikes)
                                    │
                                    ▼
                        📈 NewRTDashboard_1 (live)
```

---

## 🖼️ Screenshots & Descriptions

| # | Preview | Component | Detailed Description |
|:-:|:-------:|:----------|:---------------------|
| 1️⃣ | <img src="images/01-eventstream-pipeline-overview.png" width="320"/> | **Eventstream Pipeline Overview** | Overview of the `Bicycle_Data` Eventstream showing the full topology: the `Bicycles` source, the `Bicycle_Data-stream`, the `GroupBystreet` operator (tumbling window, sum of `No_Bikes`) and two active Eventhouse destinations. |
| 2️⃣ | <img src="images/02-eventstream-topology-raw-vs-aggregated.png" width="320"/> | **Raw vs Aggregated Data Paths** | Highlights the two parallel paths: raw events sent directly to `Eventhouse`, and pre-aggregated bike availability per street sent to `Eventhouse1`. All components are *Active*. |
| 3️⃣ | <img src="images/03-real-time-dashboard-bikepoints.png" width="320"/> | **Real-Time Dashboard** | `NewRTDashboard_1` with a 15-minute time range: a station table (ID, street, area, coordinates, bike and dock counts), a donut chart of BikePoints and an Azure Maps visual. Tiles refresh automatically. |
| 4️⃣ | <img src="images/04-eventhouse-system-overview.png" width="320"/> | **Eventhouse System Overview** | `EvenH016` storage metrics: 2.6 MB original size compressed to 104.9 KB (~25× compression), Premium cache at 100%, and the KQL database ready for querying. |

---

## 🧰 Tech Stack

| Layer | Technology |
|:------|:-----------|
| 🌊 Ingestion | Fabric Eventstream |
| ⚙️ Processing | Group By operator (Tumbling window) |
| 🗄️ Storage | Eventhouse / KQL Database |
| 🔎 Querying | Kusto Query Language (KQL) |
| 📊 Visualization | Real-Time Dashboard (Azure Maps, charts, tables) |

---

## ✨ Key Features

- ✅ Real-time ingestion with no manual refresh
- ✅ Dual-path design: raw data + aggregated data
- ✅ High compression ratio in Eventhouse storage
- ✅ Live geospatial and tabular monitoring

---

## 👤 Author

**Akram Brahem** · Data Analyst (PL-300)
🔗 [LinkedIn](https://www.linkedin.com/) · 💻 [GitHub](https://github.com/)

<div align="center">⭐ If you like this project, give it a star! ⭐</div>
