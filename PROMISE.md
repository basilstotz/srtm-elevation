## Slope and Promise

##### Slope

```js

if(this._resolution == 1){
     dx = 30
} else {
     dx = 90
}
dy = dx;

dzdx = v00 - v10;
dzdy = v01 - v11;

slope = Math.sqrt(dzdx*dzdx + dzdy*dzdy) / dx;
aspect = Math.atan2(dzdy, dzdx)

elevation=avg(v1, v2, rowFrac);

return { ele: elevation, slope: slope, aspect: aspect }

```

##### Promise

https://stackoverflow.com/questions/22519784/how-do-i-convert-an-existing-callback-api-to-promises

```js
function getElevationPromise(tileset, lat, lon, options={}){
    return new Promise( function(resolve, reject){
        tileset.getElevation( [lat,lon] , function(err, elevation){
            if(err){
                reject(err)
            }else{
                resolve(elevation)
            }
        }, options);
    });
}
```

An example:

```js
const TileSet = require('srtm-elevation').TileSet;

tileset = new TileSet('./data');

let lat=47.5;
let lon=7.5;

let ans = await getElevationPromise(tileset, lat, lon);

console.log(`ele=${ans.ele} slope=${ans.slope} aspect=${ans.aspect}`);
```
