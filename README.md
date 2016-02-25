# gtran-csv

convert geojson to csv file and backwards

This is a sub-project of [gtran](https://github.com/haoliangyu/gtran).

## Installation

```javascript
npm install gtran-csv
```

## Functions

* **setPromiseLib(object)**

    Specify the promise library. If not, the library will use the native Promise.

* **fromGeoJson(geojson, fileName)**

    Save the geojson into the given file name.

* **toGeoJson(fileName, options)**

    Read the given file into geojson.

    options:

    * mapping    -   Map csv columns to geojson attributes. Specifically, geographic coordinates are required:

    ``` javascript
    {
        x: 'x_column_name',
        y: 'y_column_name'
    }
    ```

## Use Example

```javascript
var csv = require('gtran-csv');

// if specific promise library is needed
csv.setPromiseLib(require('bluebird'));

// Read CSV file
csv.toGeoJson('source.csv')
.then(function(object) {
    var geojson = object;
});

// Save geojson into CSV file
csv.fromGeoJson(geojson, 'point.csv', {
    mapping: { x: 'longitude', y: 'latitude'}
})
.then(function(fileName) {
    console.log('CSV file has been saved at:' + fileName);
});

```
