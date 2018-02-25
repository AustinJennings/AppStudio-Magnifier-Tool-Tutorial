# Tutorial for Enabling Magnifying Tool in AppStudio Applications.

For this project, I built a custom mobile map application using Esri's App Studio and the ArcGIS Runtime SDK for Qt.  I focus on one specific feature that can be added to mobile geospatial applications - The Magnifying Tool.  By enabling this tool, users can tap and hold a location on the map to get a closer view.  They can also tap and pan thier finger across the map to move the magnifier.


## Getting the Software

To build your own applications, you will need to [install AppStudio](http://doc.arcgis.com/en/appstudio/download/).


### Other Tools

There are many other application features available for building custom mobile geospatial applications in AppStudio.  If you would like to explore what all is possible, download the [ArcGIS Runtime SDK for Qt](http://www.arcgis.com/home/search.html?t=content&q=tags:QmlSampleApplicationCurrent&content=all). 

Make sure you chose the appropriate operating system before you download!  SDKs, or software development kits, are sets of tools taht allow for the creation of applications within certain software packages or frameworks.

Once you unzip this file, simply double click the SDK application to run it.  You can view several of the functional categories using the menu on the left, and select from any of the features to view descriptions, code snippets, and more!

To view the building blocks used in this project, launch the SDK, click the three layer sandwich menu button on the left, select 'Display Information', and then click 'Show Callout'.


## Using the Magnifier

While this tool works best on features and basemaps with a high level of detail (like orthophoto or hillshade), it can be used in any application.

To get the tool to work, simply tap and hold (or click and hold on desktops) the location you wish to view closer.  A crosshair with a circular magnifying lens will appear, and inside it the imagery will be larger.

To move the tool, simply pan (or move the mouse) while continuing to touch (or click).

To remove the tool, simply lift your finter (or unclick).

Pretty schnazzy!

![](screenshot1.jpg)
![](screenshot2.jpg)

## Putting the Magnifier in your App

This nifty tool can be added with a single line of code!

Within your MapView settings, simply add the following:

```
magnifierEnabled: true
```

That's it!  Your final code should look something like this (for full code, see MagnifierTool.qml):
```
MapView {
	id: mapView
	anchors.fill: parent

	\\ here, we enable the magnifier
	magnifierEnabled: true

	Map {....map info...
	}
}
```

## Acknowledgement

Thank you to Michael-Tims et all, for your original [GitHub tutorial]().