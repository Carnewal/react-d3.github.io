Area Stack Zoom:

<div id="area-stack" class="demo"></div>
<script src="/react-d3-example/dist/simple/min/area_stack_zoom.min.js"></script>

```js
"use strict";

var React = require('react');
var ReactDOM = require('react-dom');
var AreaStackZoom = require('react-d3-zoom').AreaStackZoom;

(function() {
  var generalChartData = require('dsv?delimiter=,!../data/stack_test.csv')

  var parseDate = d3.time.format("%m/%d/%y").parse;

  var width = 700,
    height = 400,
    title = "Stack Area Chart",
    chartSeries = [
      {
        field: "Group1",
        name: "Group 1"
      },
      {
        field: "Group2",
        name: "Group 2"
      },
      {
        field: "Group3",
        name: "Group 3"
      }
    ],
    x = function(d) {
      return parseDate(d.date);
    },
    xScale = 'time';

  ReactDOM.render(
      <AreaStackZoom
        title= {title}
        data= {generalChartData}
        width= {width}
        height= {height}
        chartSeries = {chartSeries}
        x= {x}
        xScale= {xScale}
      />
  , document.getElementById('area-stack')
  )
})()
```
