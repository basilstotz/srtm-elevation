### Promise

https://stackoverflow.com/questions/22519784/how-do-i-convert-an-existing-callback-api-to-promises

```
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

```
tileset= new TileSet('./data');

let lat=47;
let lon=7;

let ans= await getElevationPromise(tileset,lat,lon);

console.log(`ele=${ans.ele} slope=${ans.slope} aspect=${ans.aspect}`);
```
