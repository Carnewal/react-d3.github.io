Scatter Plot Zoom:

<div id="scatter-garbage" class="demo"></div>
<script src="/react-d3-example/dist/simple/min/scatter_garbage_zoom.min.js"></script>

```js
"use strict"

var React = require('react');
var ReactDOM = require('react-dom');
var ScatterZoom = require('react-d3-zoom').ScatterZoom;

(function() {
  // load your general data
  var chartData = require('dsv?delimiter=,!../data/garbage.csv');

  // your date format, use for parsing
  var parseDate = d3.time.format("%YM%m").parse;

  var width = 700,
    height = 300,
    margins = {top: 50, right: 100, bottom: 50, left: 100},
    title = "Taiwan refuse disposal - Multi line",
    // chart series,
    // field: is what field your data want to be selected
    // name: the name of the field that display in legend
    // color: what color is the line
    chartSeries = [
      {
        field: 'total',
        name: 'Total',
        symbol: 'diamond',
        symbolSize: 6
      },
      {
        field: 'incineration',
        name: 'Incineration',
        symbol: 'cross',
        symbolSize: 6
      },
      {
        field: 'garbageBury',
        name: 'Garbage Bury',
        symbol: 'triangle-down',
        symbolSize: 6
      }
    ],
    // your x accessor
    x = function(d) {
      return parseDate(d.month);
    },
    xScale = 'time';

  ReactDOM.render(
      <ScatterZoom
        title= {title}
        data= {chartData}
        chartSeries= {chartSeries}
        width= {width}
        height= {height}
        margins= {margins}
        x= {x}
        xScale= {xScale}
      />
  , document.getElementById('scatter-garbage')
  )
})()
```
