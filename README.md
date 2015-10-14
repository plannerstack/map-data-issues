# map-data-issues

This repository is for the reporting of Map-data-issues regarding OSM & OTP.

#OpenTripPlanner 

**DEBUG layer**

Otp has a debug layer which can help you identify issues and anaylze logic behind trip planning
To enable debug layers:
1. Go to planner.plannerstack.com or a trip url.
2. At the end of the url ad: /?debug_layers=true
3. At the top right corner multiple layers can now be selected:https://cloud.githubusercontent.com/assets/10044515/10483652/c56e8986-7280-11e5-8546-70e96691c985.png
4. you can select: 
    a) Wheelchair acces: Every path or place which is wheelchair accesible
    b) Bike safety: All paths where travel by bike is possible
    c) Travel permissions: Shows all the path accesible by foot which might not be on the map. For example how to get around a train station etc.

#OpenStreetMap
OpenStreetMap is an openly licensed map of the world being created by volunteers and is editable by everyone who wants to contribute

**How to edit OSM**

Everybody can edit Openstreetmap. Following is a list of editors which can help you edit OSM data. The first one(ID) is the one currently used by default on openstreetmap.org

##List of OSM editors

###Online editors

####iD

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

####Potlatch 2

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


###Desktop and offline

####JOSM

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

####Merkaartor

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

###Mobile

####Vespucci

**Summary**

Vespucci is the first OpenStreetMap-Editor for Android and has been available and developed since 2009.

**Pros**
- Mobility.
- A full editor for OpenStreetMap that works both on small (phones) and large (tablet) screen android devices.
- Supports edtiting with keyboard and mouse if available.
- Create/edit Nodes, Ways, Tags, and Relations, with all the usual geometry related operations.
- built-in support for Imagery Offset Database

####OsmAnd

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

##When is OSM updated

The various map layers are updated at different frequencies.
- The "standard" map is updated very frequently; the exact time depends on how often the area is viewed by users
- The "cycle" map is updated every few days
- The "transport" map is updated every day or two
- The "MapQuest Open" map update is unclear how often this occurs at the moment
- The "Humanitarian" map update is unclear how often this occurs at the moment

##Short about interpretation of OSM in OTP*

#FAQ
