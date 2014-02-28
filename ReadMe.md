Leaflet.fullcanvas
=====================

Provides implementation of points using canvas.

*Requires Leaflet 0.7.0 or newer.*

## Using the plugin

* For canvas with points: [Demo](http://cyrilcherian.github.io/Leaflet-Fullcanvas/demo/Canvas-With-Points.html)
* For canvas with lines connecting points: [Demo](http://cyrilcherian.github.io/Leaflet-Fullcanvas/demo/Canvas-With-Lines.html)
* For canvas with points using illuminate: [Demo](http://cyrilcherian.github.io/Leaflet-Fullcanvas/demo/Canvas-With-Illuminate-Points.html)
* For canvas with points and popups: [Demo](http://cyrilcherian.github.io/Leaflet-Fullcanvas/demo/Canvas-With-Points-Poups.html)


## Usage

# How to set data.

Create your map example:

```javascript
 var map = L.map('map').setView([0, 35], 3);
     L.tileLayer('http://{s}.tile.cloudmade.com/7c2ed2e9170441289176d725eb0ca615/999/256/{z}/{x}/{y}.png', {
         maxZoom: 18
     }).addTo(map);
```
Create instance of the plugin canvas layer and add it to the map example:
```javascript
    points = [];
    //make points slat denotes latitude slon denotes longitude
    points.push({"slat": -33.3042, "slon": 26.5328});
    //make another point slat denotes latitude slon denotes longitude
    points.push({"slat": -25, "slon": 29});
    //make a canvas layer
    var layer = new MyLayer();
    //add points to the layer
    layer.setData(points);
    //add canvas layer to the map
    layer.addLayerTo(map);
```

# How to add data.

# How to color your own points.

# How to show popup.

# how to draw lines between points.
