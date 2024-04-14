# Geo IP Data Ingestion + Log Analystics Workspace and Microsoft Sentinel (SIEM) Setup

<h2>Purpose</h2>

- Ingest geographic data CSV file into Log Analytics Workspaces to derrive geolocation from IP addresses. These values will be plotted on a map for visual display later on.
- Set up a Log Analytics Workspace (LAW) instance.
- Set up a Microsoft Sentinel instance and connect the LAW to it.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/geo-ip-data-images/main/Geo%20IP%20Watch%20Data%20%2B%20Log%20Analytics%20%2B%20Sentinel%20Diagram%203.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/geo-ip-data-images/main/Geo%20IP%20Watch%20Data%20%2B%20Log%20Analytics%20%2B%20Sentinel%20Diagram%202.png"/>

#
<h3>Download the Geo-Data File</h3>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/geo-ip-data-images/main/1.png"/>

Download the Geo-Data File from the following link: https://github.com/joshmadakor1/Cyber-Course-v2/blob/main/Sentinel-Maps(JSON)/geoip-summarized.csv

#
<h3>Creating a Log Analytics Workspace Instance</h3>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/geo-ip-data-images/main/2.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/geo-ip-data-images/main/3.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/geo-ip-data-images/main/4.png"/>

Create a Log Analytics Workspace with the name “LAB-Cyber-Lab-0x”. Replace the x with the number of your choice.

You can technically name this whatever you want, this is just a sample name.

#
<h3>Creating a Microsoft Sentinel instance and connecting the LAW</h3>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/geo-ip-data-images/main/5.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/geo-ip-data-images/main/6.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/geo-ip-data-images/main/7.png"/>

Create a Microsoft Sentinel instance and connect the Workspace to it.

I had already connected mine so it does not show here (second screenshot).

You only need to select it and click “Add”.

#
<h3>Ingesting the Geo-Data CSV file into Microsoft Sentinel</h3>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/geo-ip-data-images/main/8.png"/>

Select the workspace, scroll down to “Watchlist” and select “+ New”.

This is where the Geo IP Watch Data is ingested.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/geo-ip-data-images/main/9.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/geo-ip-data-images/main/10.png"/>

Input the following values exactly so consistency is maintained for future queries:
- name/alias: geoip
- Source type: Local File
- Number of lines before row: 0
- Search Key: network

Upload the CSV file downloaded previously.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/geo-ip-data-images/main/11.png"/>

The whole file will take 20 - 40 minutes to ingest.

There are around 55k worth of items in total, so you’ll know ingestion is done when the indicator reaches that mark.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/geo-ip-data-images/main/12.png"/>

Go back to the Log Analytics workspace. Select the workspace created prior and go to Logs.

Run the query: 
  GetWatchlist(“geoip”)
  | count

You should get a result of the total item count.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/geo-ip-data-images/main/13.png"/>

You can also run GetWatchlist(“geoip”) for a list of the items themselves.

