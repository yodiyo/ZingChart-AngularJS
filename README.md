#ZingChart-AngularJS
[![Code Climate](https://codeclimate.com/github/zingchart/ZingChart-AngularJS/badges/gpa.svg)](https://codeclimate.com/github/zingchart/ZingChart-AngularJS)[![Build Status](https://travis-ci.org/zingchart/ZingChart-AngularJS.svg)](https://travis-ci.org/zingchart/ZingChart-AngularJS)
---
An AngularJS directive for ZingChart
### Install
```
bower install zingchart-angularjs
```

Inject into your app...
```
var app = angular.module('myApp', ['zingchart-angularjs']);
```

###Usage
---
_javscript_
```js
//In an Angular Controller
$scope.myValues = [5,6,3,2,3];
```

_markup_
```html
<zingchart id="chart-1 zc-values="myValues"></zingchart>
```

###Options
---
The ZingChart Component takes the following attributes:

#####_zc-id_ [string] ```(required)```
The id for the DOM element for ZingChart to attach to.

#####_zc-values_ [array] ```(optional)```
```default : null```

Either a single-dimensional or multi-dimensional array containing the values to be charted. **Must be an Angular scope variable to bind to the directive** Overrides the series values in the zc-render and zc-data objects.
```
$scope.myData = [0,2,2,3,3,4];
$scope.myData2 = [[45,43,26],[0,1,5,3]];
```
This parameter simulates the values parameter in each series object in a ZingChart json.
```js
//ZingChart json example
data:{
    series : [
        {'values' : [45,43,26]},
        {'values' : [0,1,5,3]}
    ]
}
```
The directive takes care of the work so you don't have to create this object

#####_zc-json [object] ```(optional)```
```default : null```

A ZingChart json object. This is the same object you would use to configure a chart using zingchart.render.data. It is a pseudo-parent object of zc-values. More information : http://www.zingchart.com/docs/json-attributes-syntax/
```js
//Example
$scope.json = {
  "series":[
        {
            "line-color":"#900000",
            "marker":{
                "background-color":"#dc3737",
                "border-width":1,
                "shadow":0,
                "border-color":"#f56b6b"
            }
        },
        {
            "line-color":"#efe634",
            "marker":{
                "background-color":"#fff41f",
                "border-width":1,
                "shadow":0,
                "border-color":"#fdffc0"
            }
        },
    ]
}
```
Note: You can add series values into this object like you normally would while using ZingChart. However if you define the directives zc-values parameter, those values will override and "values" inside of your zc-data object


#####_zc-render_ [object] ```(optional)```
```default : null```

A ZingChart render object. This is the same object you would use to configure a chart using zingchart.render. You can change the render type, add events, and change other zingchart properties in here. Acts like a pseudo-parent of zc-values and zc-data. zc-render's properties will be overwritten if zc-values and zc-data are defined. More information : http://www.zingchart.com/docs/reference/zingchart-object/#zingchart__render

Note: This object will not be watched inside the directive. It is a one-time setup.

```
//Example
{
    output :'canvas',
    events: {
        complete : function(p) {...}
    }
}
```



#####_zc-height_ [number] ```(optional)```
```default : 400```

Will override the height inside of a zc-render object if defined.

#####_zc-width_ [number] ```(optional)```
```default : 600```

Will override the width inside of a zc-render object if defined.

#####_zc-type_ [string] ```(optional)```
```default : line```

Will override the render type inside of a zc-render and zc-data object if defined.
