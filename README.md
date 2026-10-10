. 01-eventstream-pipeline-overview.png

Title: Eventstream Pipeline – Source to Eventhouse Destinations (Active State)

Description:
Overview of the Microsoft Fabric Eventstream Bicycle_Data in the real-time workspace. The canvas shows the end-to-end streaming topology:

Source: Bicycles (sample bike-sharing data feed), status Active.
Stream: Bicycle_Data-stream, the default stream that ingests events from the source.
Operator: GroupBystreet, a Group By transformation using a Tumbling window that computes the sum of No_Bikes per street.
Destinations: two Eventhouse destinations (Eventhouse and Eventhouse1), both Active. One receives the raw stream directly, the other receives the aggregated output of the operator.

The left-hand panel lists all components (Sources, Streams, Operators, Destinations) for easy navigation.

2. 02-eventstream-topology-raw-vs-aggregated.png

Title: Eventstream Topology – Raw Ingestion and Aggregated Output Branches

Description:
Alternative view of the Bicycle_Data Eventstream with the Bicycles source selected. It highlights the two parallel data paths:

Raw path: Bicycle_Data-stream → Eventhouse, storing every incoming event for detailed analysis.
Aggregated path: Bicycle_Data-stream → GroupBystreet (tumbling window, sum of No_Bikes) → Eventhouse1, storing pre-aggregated bike availability per street.

This design separates granular event data from analytics-ready aggregates, enabling both detailed KQL queries and fast dashboard visuals. All components are Active, confirming data is flowing in real time.

3. 03-real-time-dashboard-bikepoints.png

Title: Real-Time Dashboard (NewRTDashboard_1) – BikePoints Monitoring

Description:
Real-Time Dashboard built in Microsoft Fabric on top of the Eventhouse KQL database, with the time range set to Last 15 minutes. It contains:

Table visual: station-level details (BikePoint ID, street name, area such as Old Ford and St John’s Wood, latitude, longitude, and bike/dock counts), limited to 10 rows.
Donut chart: distribution of the 10 monitored BikePoints, each at 10.0%.
Map visual: geospatial view of station locations powered by Azure Maps, with Auto center enabled.

All tiles refresh automatically (1m ago), providing a live operational view of the bike-sharing network.

4. 04-eventhouse-system-overview.png

Title: Eventhouse EvenH016 – System Overview and Storage

Description:
System overview page of the Eventhouse EvenH016, which hosts the KQL database of the same name and serves as the analytics store for the streaming data. It shows:

Storage metrics: original size of 2.6 MB, compressed to 104.9 KB (a compression ratio of roughly 25×).
Cache usage gauge showing 100% in the Premium tier.
Navigation: System overview, Databases, Monitoring, and the KQL database list.

This confirms that the ingested events are successfully persisted and ready for querying with KQL and for visualization in the dashboard.
