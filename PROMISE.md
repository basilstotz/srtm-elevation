### Promise

https://stackoverflow.com/questions/22519784/how-do-i-convert-an-existing-callback-api-to-promises

```js
function getElevationPromise(tileset,lat,lon){
    return new Promise( function(resolve,reject){
        tileset.getElevation( [lat,lon] , function(err,elevation){
            if(err){
                reject(err)
            }else{
                resolve(elevation)
            }
        });
    });
}
```

An example:

```js
const TileSet = require('srtm-elevation').TileSet;

tileset = new TileSet('./data');

let lat=47.5;
let lon=7.5;

let ans = await getElevationPromise(tileset,lat,lon);

console.log(`ele=${ans.ele} slope=${ans.slope} aspect=${ans.aspect}`);
```
