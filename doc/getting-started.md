# Getting Started

The document contains a quick tutorial of creating a basic map object on HTML page. 

## Prerequisites

To create a map object, you will be required to prepair at least one of following assets:

* Background
* Foreground
* Cursor

Each of your asset file should consist of one or more tiles, which probably looks like this:

![background.png](https://rvhuang.github.io/rpg-map-factory/samples/rpg-map-editor/images/background.png)

In this example, the size of each tile is 32 \* 32 pixels. The asset will be used to render each tile on map in following steps. 

## Creating Map Instance

Following HTML/JavaScript snippets show how to turn a `canvas` element into a controllable map object. The size of map is 60 \* 32 tiles. 

```html
<canvas id="myCanvas"></canvas>
```

```javascript
var tileSize = 32; // The unit is pixel. 
var mapWidth = 60; // The unit is tile.
var mapHeight = 32; // The unit is tile.
var mapFactory = new MapFactory("myCanvas", mapWidth, mapHeight, tileSize, tileSize);
```

By default, the instance is **responsive** -- the width and height of `myCanvas` element will be adjusted to fit the size of parent element.

## Assigning Asset Mapping Callback

Now we need to tell the map instance what background tile we want to show. In following snippet, we assign [background.png](https://rvhuang.github.io/rpg-map-factory/samples/rpg-map-editor/images/background.png) and an asset mapping callback function to the instance. 

```javascript 
    mapFactory.backgroundAsset('images/background.png');
    mapFactory.backgroundAssetMapping(function (i, j) {    
        // i and j are the coordinates of current tile to be displayed.
        // The unit is tile.
        // x and x are the left-top position on 'background.png'. 
        // The unit is pixel.
        return { 
            x: 7 * tileSize, 
            y: 3 * tileSize  
        }; // Default background tile is the right-bottom one on 'background.png'.
    });
```

When callback function is invoked, it informs `MapFactory` instance that the image of current tile (*i* and *j*) starts at [224, 96] on [background.png](https://rvhuang.github.io/rpg-map-factory/samples/rpg-map-editor/images/background.png).

Now a responsive controllable map object is on your page. 

## See Also

* [RPG Map Editor](https://rvhuang.github.io/rpg-map-factory/samples/rpg-map-editor/index.html) - the complete sample.  
* [API Reference](api-reference.md) - learn more detail about `MapFactory` class. 
