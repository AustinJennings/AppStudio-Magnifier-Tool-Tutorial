# Tutorial for Enabling Magnifying Tool in AppStudio Applications.

For this project, I built a custom mobile map application using Esri's App Studio and the ArcGIS Runtime SDK for Qt.  I focus on one specific feature that can be added to mobile geospatial applications - The Magnifying Tool.  By enabling this tool, users can tap and hold a location on the map to get a closer view.  They can also tap and pan thier finger across the map to move the magnifier.


## Getting the Software

To build your own applications, you will need to [install AppStudio](http://doc.arcgis.com/en/appstudio/download/).


### Other Tools

There are many other application features available for building custom mobile geospatial applications in AppStudio.  If you would like to explore what all is possible, download the [ArcGIS Runtime SDK for Qt](http://www.arcgis.com/home/search.html?t=content&q=tags:QmlSampleApplicationCurrent&content=all). 

Make sure you chose the appropriate operating system before you download!  SDKs, or software development kits, are sets of tools taht allow for the creation of applications within certain software packages or frameworks.

Once you unzip this file, simply double click the SDK application to run it.  You can view several of the functional categories using the menu on the left, and select from any of the features to view descriptions, code snippets, and more!

To view the building blocks used in this project, launch the SDK, click the three layer sandwich menu button on the left, select 'Display Information', and then click 'Show Callout'.

## Building an Application

While this tool can be applied to existing projects using simple code, we will also walk through creating a simple map application for this tutorial.  Follow the steps below:

1. Launch AppStudio (on desktop, not web). 
(Note: if you wish to publish this application, you will also need to sign in with an ArcGIS Online account using the button at the top right of the AppStudio window)

2. Click on the New App button in the top toolbar.

3. Select the Hello World (Runtime) tile.

4. Type in your desired application name in the Title bar to the right.

5. Click Create.

You will now be taken back to the AppStudio for ArcGIS dashboard.  If you select your new application tile from the list of available applications, you will get a menu bar along the right with buttons for Settings, Run, Edit, etc...

To test out your new application, use the Run button.  Go ahead, take it for a spin (you know you want to)!

## Editing your Application and Adding the Magnifier Tool

This nifty tool can be added with a single line of code!

All you need to do is access the Qt IDE by selecting the Edit button ({;}) next to Run in the right-hand menu bar.

Within your MapView settings, simply add the following under the MapView heading:

```
	MapView {
		id:mapView

		// add code
		magnifierEnabled: true

		anchors{
			//.... the rest of your code goes here ...
		}
	}
```

That's it!  You're all done.  But we want to make sure we have something go magnify, so let's change a few additional settings to get a basemap that contains imagery instead of the standard topo:

1. Under your MapView heading, locate the Map{ section.
2. Change the BasemapTopography{} to BasemapImageryWithLabels{}
3. Under the basemap heading you just changed, change the viewpoint settings (x and y) to a location that is interesting to you.  I chose an airfield similar to the one used in the SDK docs.

```
        // add a basemap (I chose imagery for more detail)
        Map{
            id:map

            BasemapImageryWithLabels{}
            onLoadStatusChanged: {
                if (loadStatus === Enums.LoadStatusLoaded) {
                        mapView.setViewpoint(initialViewpoint);
                }
            }
        }
        ViewpointCenter {
            id: initialViewpoint
	    
	    // I changed the viewpoint to an airfield for a more interesting view.
            center: Point {
                x: -110.8258
                y: 32.1545089
                spatialReference: SpatialReference {wkid: 4326}
            }
            targetScale: 2e4
        }
    }

```


Now, save your changes, close out the Qt IDE, reopen your AppStudio window and launch the application.

## Using the Magnifier

While this tool works best on features and basemaps with a high level of detail (like orthophoto or hillshade), it can be used in any application.

To get the tool to work, simply tap and hold (or click and hold on desktops) the location you wish to view closer.  A crosshair with a circular magnifying lens will appear, and inside it the imagery will be larger.

To move the tool, simply pan (or move the mouse) while continuing to touch (or click).

To remove the tool, simply lift your finter (or unclick).

Pretty schnazzy! You've just created or modified an application using QML language!

![](screenshot1.jpg)
![](screenshot2.jpg)


## Acknowledgement

This information was modified from the [ArcGIS Runtime SDK documentation site](https://developers.arcgis.com/qt/latest/qml/sample-code/sample-qt-showmagnifier.htm).
