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
    //make points slat denotes the latitude and slon denotes the longitude
    points.push({"slat": -33.3042, "slon": 26.5328});
    //make another point slat denotes the latitude and slon denotes the longitude
    points.push({"slat": -25, "slon": 29});
    //make a canvas layer
    var layer = new MyLayer();
    //set the data points to the layer
    layer.setData(points);
    //add canvas layer to the map
    layer.addLayerTo(map);
```

# How to add data.

To add data live into the map:
To the canvas layer created, you can add points

```javascript
    //add points to the layer...here slat denotes the latitude and slon denotes the longitude
    layer.setData({"slat": -33.3042, "slon": 26.5328});
```

# How to color/create your own points.

You can color/create your own points by overriding the drawSource function example:
```javascript
    var MyLayer = L.FullCanvas.extend({
        //over riding the getsource function
        drawSource: function(point) {
            //get the context
            var ctx = layer.getCanvas().getContext("2d");
            ctx.globalCompositeOperation = "lighter";
            //drawing the shape of the point
            ctx.beginPath();
            //adding gradient 
            var grd = ctx.createRadialGradient(point.x, point.y, 0, point.x, point.y, 10);
            grd.addColorStop(0.200, 'rgba(255, 242, 0, 1)');
            grd.addColorStop(0.370, 'rgba(255, 157, 0, 1)');
            grd.addColorStop(0.5, 'rgba(255,255, 255, 1)');
            ctx.fillStyle = grd;
            ctx.arc(point.x, point.y , 2, 0, 2 * Math.PI, true);
            ctx.fill();
        }
    });
```

# How to show popup.
You can color/create your own points by overriding the drawSource function example:
```javascript
var MyLayer = L.FullCanvas.extend({
        //over riding the clickedPoints function
        clickedPoints: function(points){
            var text = "You clicked on the point Latitude["+ points[0].data.slat + "] Longitude["+ points[0].data.slon + "]";
            //show your popup
            alert(text);
        }

    });
```

# how to draw lines between points.

Create instance of the plugin canvas layer and add it to the map example:
```javascript
    points = [];
    //make points slat denotes the source latitude and slon denotes the source longitude 
    //make points tlat denotes the target latitude and tlon denotes the target longitude 
    points.push({"slat": -33.3042, "slon": 26.5328,"tlat": -10, "tlon": 15});
    //make points slat denotes the source latitude and slon denotes the source longitude 
    //make points tlat denotes the target latitude and tlon denotes the target longitude 
    points.push({"slat": -25, "slon": 29, "tlat": -50, "tlon": 10});
    //make a canvas layer
    var layer = new MyLayer();
    //set the data points to the layer
    layer.setData(points);
    //add canvas layer to the map
    layer.addLayerTo(map);
```


