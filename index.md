---
layout: default
title: Land Terrain Support
permalink: /
---

# Support

**Land Terrain: Topo & Drainage** shows where the water goes on your land, where a pond could sit and how much it would hold, how steep a driveway is, and how much water drains through a creek crossing. It works from the free 1-meter lidar elevation that the U.S. Geological Survey publishes, and every calculation runs on your iPhone or iPad.

**Land Terrain is for land in the United States.** You can use the app from any country; the land has to be in the US.

There is no account and no server of ours. Your parcels stay on your device.

---

## Contact

**developer.barseghyan@gmail.com**

I usually reply within about two business days. If a result looks wrong, please include the parcel's approximate location (a nearby town or the coordinates), what you tapped, and a screenshot. The PDF report or the map image from the app also helps, because both name the data they came from.

---

## Before anything else

**Land Terrain is a planning tool. It is not a survey and not an engineering design.** Contours, flow paths, watersheds, pond volumes, grades and pipe sizes are estimates from public elevation data. Before you build a pond, a road, a crossing or anything that depends on these numbers, verify them on site and with a licensed professional (a surveyor, an engineer, or your county or conservation district).

---

## Frequently asked questions

### Where does the elevation come from?

From the USGS 3D Elevation Program (3DEP): bare-earth lidar at 1 meter, or 2 meters for large parcels. The app downloads it directly from the USGS servers the first time you open a parcel and keeps it on your device, so every tool then works offline. Mapped streams come from the USGS National Hydrography Dataset (NHDPlus HR) and rainfall for crossings from NOAA Atlas 14.

### Does it work outside the United States?

The app does; the data does not. You can live anywhere, but the land has to be in the United States, because the elevation comes from the U.S. Geological Survey. If you are abroad, the map opens on US land and you move it to yours. Drawing, importing or exploring land anywhere else shows "This area is not available yet. Land Terrain works for land in the United States." Nothing is saved or downloaded and your free parcel is not used.

### What about Alaska, Hawaii and the territories?

All of them can be used; what differs is the elevation USGS has there. Most of Hawaii, and Puerto Rico and the U.S. Virgin Islands, have 1-meter lidar. In Alaska, Guam, the Northern Mariana Islands and American Samoa the app offers 10-meter elevation, and the pond planner, creek crossings and culverts stay off. The app checks your parcel and tells you which one you get.

### My land shows "10 m elevation". Why?

Lidar has not been flown everywhere yet. Where there is none, the app uses the USGS 10-meter elevation instead and tells you so. Slope, contours and rough flow paths still work; the pond planner, creek crossings and culverts need lidar detail and stay off on 10 m data.

### What does the confidence grade on a watershed mean?

Every watershed carries a grade from the terrain itself. On hilly and rolling land the app's watersheds matched the USGS StreamStats service within 5% at every test creek, and they are graded high. On flat, ditched farmland, culverts and tile drains under roads are invisible to the elevation data, so water can appear to go the wrong way; the app grades those watersheds low and says why. If a road crosses your creek, **Place a culvert** (Pro) lets you route the water through the road fill yourself.

### Does it work without a signal?

Yes, once the parcel's elevation is downloaded. Download it at home on Wi-Fi, then take the app out on the land. The satellite imagery under the map comes from Apple Maps and needs a connection; the analysis does not.

### The download stopped. Do I start again?

No. Tiles that already arrived are kept. Open the parcel again with a connection and the download continues where it stopped. If the USGS server is busy, the app says so; try again a little later.

### "This area is too large to analyse on a phone"

A single analysis has a size limit so that it fits in the phone's memory. Draw a tighter boundary, or split the land into two or more parcels. The message says the largest size that fits.

### How do I bring in my boundary?

Draw it on the map, use a circle around where you stand, or import a KML, KMZ, GPX or GeoJSON file (from the Files app, Mail or AirDrop, or with **Open in Land Terrain**). Parcels you plot in **Deed to Map** appear under **Add your land › From Deed to Map**.

### How much space does it use, and how do I free it?

Each parcel keeps its elevation on the device, usually a few to a few dozen megabytes. **Settings › Storage** shows the total and can clear it. Your parcels and saved work stay; the elevation downloads again the next time you open a parcel.

### Metric or US units?

**Settings › Units.** The whole app, the PDF report and the exports follow the one system you choose.

### What is free, and what does Pro add?

Free: one parcel with the Terrain, Water and Slope layers, Explore (look at any spot without saving it) and the map image. **Land Terrain Pro** is a one-time purchase that adds unlimited parcels, the pond planner, driveway profiles, creek crossings, Place a culvert, the PDF report and exports (KMZ, KML, GeoJSON, GPX, CSV) and 2 ft contours. The price is shown in the app and on the App Store. There is no subscription.

### I bought Pro, but the app shows it locked.

Open **Settings › Land Terrain Pro › Restore purchases** (also on the Pro screen), signed in with the same Apple Account you bought it with. Pro is shared with your Family Sharing group, so family members can restore it the same way.

### How do I get a refund?

Purchases are handled by Apple. Request a refund at [reportaproblem.apple.com](https://reportaproblem.apple.com). A refund returns the app to its free features; it never deletes your parcels.

---

## Privacy

No account, no analytics, no advertising, and nothing is collected. Read the [Privacy Policy]({{ site.baseurl }}/privacy).

---

[Privacy Policy]({{ site.baseurl }}/privacy) · [Terms of Use]({{ site.baseurl }}/terms)
