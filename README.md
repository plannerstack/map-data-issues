# Welcome to the map-data-issues

This repository is for the reporting of Map-data-issues regarding OSM & OTP. Together we build on the improvement of the data we use to travel. We created this repository to explain how we work and how you maybe can contribute to the improvements.

* You can report issues based on our [issue template](https://github.com/plannerstack/map-data-issues/blob/master/Issue%20template.md)
* You can check out the status of the [different issues](https://github.com/plannerstack/map-data-issues/issues)
* You can add tags to issues to bundle the types of issues
* You can help along fixing issues by editting OSM, for that we have some tips and tricks below!

# Table of Content

<!-- MarkdownTOC -->

- [How to create routes and find issues using OTP](#how-to-create-routes-and-find-issues-using-otp) 
	- [How to find GTFS stoplinker data issues](#how-to-find-gtfs-stoplinker-data-issues)
- [Different kinds of issues](#different-kinds-of-issues)
- [Tips & Tricks](#tips--tricks)
	- [OpenTripPlanner debugging](#opentripplanner-debugging)
	- [Short about interpretation of OSM in OTP](#short-about-interpretation-of-osm-in-otp)
	- [OpenStreetMap](#openstreetmap)
- [FAQ](#faq)
	- [How long does it take before my OSM changes result in awesome new trips in OTP?](#how-long-does-it-take-before-my-osm-changes-result-in-awesome-new-trips-in-otp)

<!-- /MarkdownTOC -->

# How to create routes and find issues using OTP
Errors occur in the maps using OpenTripPlanner (OTP) or OpenStreetMap (OSM). Issues that occur are for example walking routes, missing connections, positioning of stations, GTFS-lines and missing exits. In this document trip planning is explained, how to find which issues and already some tips on how they could possibly be solved. But before explaining the different issues first is explained how to actually find issues using OpenTripPlanner.

## Create a trip and find the Stop link issue
Issues can be found using different sources. First, start by making a trip in OTP. So far we mainly focused on train routes in The Netherlands. To start you set the starting point by clicking the right mouse button and choose: Set as Start Location (figure 1). Then go in either direction along the railroad and set the End Location close to another train station. 

![schermafbeelding 2015-11-11 om 12 19 35](https://cloud.githubusercontent.com/assets/15247075/11089986/8d9ac0d4-886e-11e5-93d5-b0a8ce9701f3.png)

OTP then calculates a route between the two set locations.

![weesp-almere](https://cloud.githubusercontent.com/assets/15247075/11089940/43955c10-886e-11e5-941e-64361c5ba063.png)

Zoom in on one of the stations to have a better look. Most of the times nothing strange appears, however sometimes one can see that something must be incorrect. For example in figure 3 where a trip is created to a destination close to the station. When having a good closer look at the image a long walk (grey line) is supposed to be made to reach the End Location. However, the icon of the train station is next to the red flag of the End Location and under the red line (GTFS train line). The assumption arises that something has to be incorrect in this situation. 

![almere poort](https://cloud.githubusercontent.com/assets/15247075/11089936/43914f6c-886e-11e5-96c5-68e95a88de20.png)

The problem that occurred here is that the red line from the train probably has a stop link in the incorrect place. The suggestion already occurred when looking at the map, however a double check is done through Google Streetview. The result of this issue is an unnecessary 700-meter walk from an impossible place to leave the train and platform. In order to change this the stop link should be placed close to the train station where the platforms are. 

Now we know how to create a trip and how to recognize an issue. Lets see which other issues can occur when creating train routes in OTP besides the station positioning issue that occurred at Almere Poort.
For all stop linker issues, check here: [Stop link issues](https://github.com/plannerstack/map-data-issues/issues?q=is%3Aissue+is%3Aopen+label%3A%22Stop+linkers%22)

##How to find GTFS stoplinker data issues
1. download [GTFS data set](http://docs.plannerstack.org/en/latest/#getting-the-dutch-public-transport-schedules)
![plannerstack data](https://files.slack.com/files-pri/T0762D7HQ-F0L2QJ8JZ/pasted_image_at_2016_02_02_02_54_pm.png)
2. unzip it [foto](file:///Users/jesse_harting/Downloads/Pasted%20image%20at%202016_02_02%2002_54%20PM.png)
3. open stops.txt
4. Find station 
5. Find stations latitude longitude (latlong)
6. paste it in google
When you have found some incorrect latlong's, paste them underneath the right issue. 

# Different kinds of issues
* [Missing intersections at Hilversum](#missing-intersections-at-hilversum)
* [GTFS shape lines missing in Heerlen](#gtfs-shape-lines-missing-in-heerlen)
* [No public transport routes in Winterswijk](#no-public-transport-routes-in-winterswijk)
* [Extended walking routes in Geleen-Lutterade](#extended-walking-routes-in-geleen-lutterade)
* [Maximum walking distance settings in Rotterdam](#maximum-walking-distance-settings-in-rotterdam)
* [Wrong exits in Susteren](#wrong-exits-in-susteren)
* [Road connections missing in Nijmegen](#road-connections-missing-in-nijmegen)

Some of the issues might look the same, however they are slightly different and all have different impact on the outcome in OTP or OSM. 

## Missing intersections at Hilversum
In the image below the suggested route at Hilversum Central Station is longer than needed because there is a connection missing in the crossing paths. When a trip is planned, OTP or OSM calculated these paths as two crossing routes that might be separated from each other, for example by a bridge. However, there is no bridge and they actually do cross on the same level. An intersection to connect both paths is missing (black dot) in OSM. Until now this route suggests you walk an extra loop, because of this missing intersection.

![hilversum walking route](https://cloud.githubusercontent.com/assets/15247075/10728071/0b943552-7bdf-11e5-8b45-6996c20686c6.png)

To make it more clear the issue in the image above is explained further, making you eventually walk to the southwest of the train station. The starting point is the end of the long red line: 
*Looking at the image above exit at the right side of the yellow lines. Instead of going left (northwest) it makes you walk right (southeast) towards the first intersection (very short walk). From there you go left (northeast) to the second intersection. There you should turn to the left again going in a southeastern direction, crossing the railroad track. Right before you cross the first railroad track, a brighter green-blue line crosses the darker one you are walking on. Where it crosses, there is no intersection (black dot) drawn. Because there is no intersection drawn, it looks like you cannot make a left turn but only continue walking in a northwest direction. That is why OSM and OTP make you walk the extra loop*. 

##GTFS shape lines missing in Heerlen
In the image below you can see a GTFS-issue. The green line is the bus going from A to B. However, in this image you can see where the green line is connecting A and B in a direct straight line, which is actually not possible. Buildings, railroads, walking areas and other objects are in between these two points, making it an impossible route. In GTFS the route should be drawn over the roads it is actually using. So when you see a line like this, it is not yet entered in the right way in GTFS. This can occur because the public transport operators are not mandatory to provide this information or if they just not provided the information.

![bus route heerlen](https://cloud.githubusercontent.com/assets/15247075/10697646/4af1fda8-79ad-11e5-9933-3feb543c379b.png)

## No public transport routes in Winterswijk
The next image shows two stations in Winterswijk. There is no connection between the start location and end location that uses public transport services. Instead of taking the train for 2 minutes this suggested route requires a 1,3 km walk. However, during week weekdays the train will run twice an hour. It also exceeds the maximum set walking distance, so it makes no sense that the train or bus connection is missing. 
![schermafbeelding 2015-11-06 om 14 11 48](https://cloud.githubusercontent.com/assets/15247075/10997888/269a9430-8491-11e5-89fa-e090cebf0374.png)

## Extended walking routes in Geleen-Lutterade
The issue here has some overlap with the missing intersection at station Hilversum and incorrect stop links (arriving at wrong side) of Almere Poort. However, there is also a walking line missing making it more difficult to reach the final destination in Geleen-Lutterade. Where the dark grey (walking route) and the light green/blue line cross, there the intersection is missing. So you have to walk all the way further to a connection that does eventually link to another path towards your final destination. However, even if the intersection was there another connection missed to make the walk shorter. Between the flag of end location and light green/blue line, there should be a walking path in the corner of the horseshoe shape and the grey line of the end location. This reduces the walk to around 100 meters instead of 600 meters as it is now. In OSM we found that one of the issues was also that pedestrians were not alloud to enter the bicycle path, which made it impossible to walk they way they were supposed to be.

![schermafbeelding 2015-11-06 om 11 53 32](https://cloud.githubusercontent.com/assets/15247075/10995474/76fff7e4-847d-11e5-843c-3345e07d3804.png)

![schermafbeelding 2015-11-06 om 11 53 21](https://cloud.githubusercontent.com/assets/15247075/10995475/7731cd3c-847d-11e5-8435-719f58a2b361.png)

## Maximum walking distance settings in Rotterdam
The maximum walk distance has much influence on the route and travel time. When the maximum walking distance is set higher, the route can change and also the travel time can change. Lets take a look at the following example and choose a final destination at around 1600 meters from the train station. 

When traveling in Rotterdam and your maximum walking distance is set at 1500meters the route is as following:

![rotterdam 2](https://cloud.githubusercontent.com/assets/15247075/11091578/2d038ec8-887c-11e5-836d-ba76d55fba49.png)

In the image above you will see that the traveling person has a short bus connection and still a long walk before reaching the final destination. The time of arrival is 10:46. In the figure 9 below you will see a different route. 

![rotterdam 1](https://cloud.githubusercontent.com/assets/15247075/11091577/2d02c452-887c-11e5-9ce5-a7f2164fce92.png)

The maximum walking distance in the image above is set at 2000 meters. The walk is a little longer, however this is only 100 meters extra. The time of arrival is 10:35. The route is 10 minutes shorter and no bus fare is needed so it is also cheaper. 

## Wrong exits in Susteren
In earlier issues the missing walking connections are explained. In this image another long walking route is created, but this has nothing to do with missing intersections. However, it does occur due to a missing connection between the platform and the exit. The exit or platform is not connected to the west side of the station, which leads to an extreme walking loop. However, there is a walking crossing over the railroad tracks which makes the actually much shorter and directly. Here, the exit should be made in both directions to avoid long walking routes.

![schermafbeelding 2015-11-06 om 11 30 30](https://cloud.githubusercontent.com/assets/15247075/10995033/549ce4ee-847a-11e5-99ce-4b4113bf89b8.png)

## Road connections missing in Nijmegen
In the image below a long walking loop is created between the exit and end location while they are next to each other. This probably occurs because the bike path and road are not connected. 

![schermafbeelding 2015-11-05 om 17 01 39](https://cloud.githubusercontent.com/assets/15247075/10973756/125724b4-83df-11e5-8652-f1e05513ff37.png)

![schermafbeelding 2015-11-05 om 17 01 31](https://cloud.githubusercontent.com/assets/15247075/10973757/127aa588-83df-11e5-8d6c-8e67f8d843d1.png)

The figure here shows that the assumption above is correct. There is no connection between the bicycle path and the road. However, through Google Streetview a pedestrian crossing is seen that connects both sides. And even without a pedestrian crossing a possibility should be to cross the street anyway to reach the final destination instead of going 100 meters left, cross the street and than come back for another 100 meters.  

# Tips & Tricks

## OpenTripPlanner debugging

**DEBUG layer**

Otp has a debug layer which can help you identify issues and anaylze logic behind trip planning
To enable debug layers:

1. Go to planner.plannerstack.com or a trip url.

2. At the end of the url ad: /?debug_layers=true

3. At the top right corner multiple layers can now be selected: [example](https://cloud.githubusercontent.com/assets/10044515/10483652/c56e8986-7280-11e5-8546-70e96691c985.png)

4. you can select: 
   
  a) Wheelchair acces: Every path or place which is wheelchair accesible

  b) Bike safety: All paths where travel by bike is possible

  c) Travel permissions: Shows all the path accesible by foot which might not be on the map. For example how to get around a train station etc.

## Short about interpretation of OSM in OTP

`@todo`


## OpenStreetMap
OpenStreetMap is an openly licensed map of the world being created by volunteers and is editable by everyone who wants to contribute

**How to edit OSM**

Everybody can edit Openstreetmap. Following is a list of editors which can help you edit OSM data. The first one(ID) is the one currently used by default on [openstreetmap](https://www.openstreetmap.org)

### List of OSM editors

#### Online editors

##### iD

**Summary**

Online editor.

**Pros**
- It is currently the pre-set editor for [Openstreetmap's](https://www.openstreetmap.org) 'Edit' tab, and runs in your web browser.
- It has a 'walkthrough' feature and has been designed to be an easy introduction for brand new OSM contributors
- Development is active and ongoing, with a lot of attention paid to user experience.
Unlike Potlatch, this doesn't require a flash plugin. It's all JavaScript and should work in most modern web browsers.
- Most of the tags and relations are hidden behind localized labels.
- Wiki help can be displayed directly in editor when editing tags
- You can use custom aerial imagery.
- mapillary photos directly available in editor
- Slide iD fork gives OSM editors access to billions of GPS tracks recorded by Strava users and allows for very precise mapping of twisted roads and trails.
**Cons**
- It's not intended for power users (who are already excellently served by JOSM) or those who want the speed of a desktop client.
- Consumes most processing power (compared with Potlatch 2 and JOSM), so if the CPU/browser is slow, lags may occur
Zooming and panning prompts a map fetch (not as fluid)
- The interface departs from normal OpenStreetMap terminology ("point", "line" and "area" instead of "node", "way" and "relation"), which can cause confusion, and editing accidents.
- It is not possible to work offline
- Does not support all browsers (I.E. in particular is not supported)

##### Potlatch 2

**Summary**

Flash online editor.

**Pros**  
- Available via the 'Edit' tab's drop-down arrow.
- As the precursor to iD (above) Potlatch was also designed for beginners and is great for quick easy immediate editing.
- Displaying of gps traces in a separate layer.
- Some advanced features including vector backgrounds and a merging/conflation functionality for specialists
- Several aerial imagery backgrounds preconfigured and option for custom TMS imagery (please check the permissions)

**Cons**
- Requires a flash plugin in the browser (in Microsoft's Edge browser enable Flash in settings)
- As with iD, it's not intended for power users
- Not as fast and fluid as a desktop client
- does not work offline


#### Desktop and offline

##### JOSM

**Summary**

JOSM offers a large set of features and useful tools for a wide range of editing styles: It will either read in GPX tracks from your hard disk, or download them from OSM. Aerial imagery can easily be downloaded as a background for tracing. JOSM also supports photo mapping and audio mapping. Once you have completed your edits, you can upload them to OSM.

**Pros**
- Fast fluid panning and zooming. Near-infinite zooming for super-precise mapping.
- Can work offline using downloaded data files, and can work with local photo and GPX files
- Advanced editing functionality e.g. make nodes of a roundabout into a circle.
- A big selection of aerial imagery and third-party gps traces immediately available as backgrounds for tracing. Custom TMS and WMS aerial imagery can be added too (please check the permissions).
- Highly configurable and extendible via plugins, Map Styles and Presets.
- Built in validator, which checks for common mapping errors before data upload
- Very active development
- Offline editing is possible
- Tags are shown to user directly. Many tags are recognized by the "presets" which then show description, a translated/localized form and links to the OSM wiki page about a tag for more info.

**Cons**
- The finer points of the interface take a while to learn.
- You have to download the software to run it, unlike the following online options (although there is a "Java Web Start" option)
- It requires Java 7+ to work.
- No help text when editing tags

##### Merkaartor

**Summary**

Merkaartor is a small editor for OpenStreetMap available under the GNU General Public License and developed using the Qt toolkit.

**Pros**
- Has some unique features like transparent display of map features like roads and true curved roads.
- Intuitive user interface
- Binaries for Windows, Mac OS X and some Linux platforms are available. Source for the rest.
- Easy to set up satellite imagery from Bing or any other WMS source.
- Tag styles can be customized
- Save rendered maps as SVG or bitmap graphic

**Cons**
- Merkaartor is under early development, which makes new and exciting features available only by grabbing the source.
- Albeit under development (and it is not bad at all) it is very memory hungry and can freeze the machine while page-swapping (lots of disk activity)
- Crashes on large data sets. Developer community is moribund.

#### Mobile

##### Vespucci

**Summary**

Vespucci is the first OpenStreetMap-Editor for Android and has been available and developed since 2009.

**Pros**
- Mobility.
- A full editor for OpenStreetMap that works both on small (phones) and large (tablet) screen android devices.
- Supports edtiting with keyboard and mouse if available.
- Create/edit Nodes, Ways, Tags, and Relations, with all the usual geometry related operations.
- built-in support for Imagery Offset Database

##### OsmAnd

**Summary**

Navigation app that allows you to add, delete or change POIs.

**Pros**
- Fully offline
- Relatively simple user interface
- Also supports Notes

**Cons**
- Node edits only
- Offline means time lag: downloaded map might be old, might take some time for user to upload changes
- Editing on a mapview, not a dataview. So you might add things that are there but not rendered.
- Usually no sat pic background, so POIs might be some distance from real location.


# FAQ

## How long does it take before my OSM changes result in awesome new trips in OTP?

* We build OTP based on the latest OSM file of the Netherlands in http://download.geofabrik.de/europe/
* If that's updated, OTP will be updated the next day
