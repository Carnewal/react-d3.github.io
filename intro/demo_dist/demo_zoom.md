# Building bar stack with zoom

`react-d3-zoom` support charts with zoom! We support all kinds of common charts such as line chart, bar chart, bar group chart... etc.


<div id="data_zoom_bar_stack" class="demo"></div>
<script src="/react-d3-example/dist/min/es5/bar_stack_zoom.min.js"></script>

```js
"use strict";

var React = require('react');
var BarStackZoom = require('react-d3-zoom').BarStackZoom;

(function() {
  // loading data
  var generalChartData = require('dsv?delimiter=,!../data/age.csv')

  // find find keys
  var ageNames = d3.keys(generalChartData[0]).filter(function(key) { return key !== "State"; });

  // add values in fields use for finding maximum value of the chart, see yDomain prop.
  generalChartData.forEach(function(d) {
    var y0 = 0;
    d.ages = ageNames.map(function(name) { return {name: name, y0: y0, y1: y0 += +d[name]}; });
    d.total = d.ages[d.ages.length - 1].y1;
  });

  var width = 700,
    height = 400,
    margins = {top: 50, right: 50, bottom: 50, left: 50},
    id = "test-chart",
    title = "Bar Stack Chart With Zoom",
    svgClassName = "test-chart-class",
    titleClassName = "test-chart-title-class",
    legendClassName = "test-legend",
    legendPosition = 'right',
    showLegend = true,
    showXAxis = true,
    showYAxis = true,
    showXGrid = true,
    showYGrid = true,
    // what fields you want to build in the chart
    // field is for the field in your csv field
    // name is for the name you want to show in your legend.
    chartSeries = [
      {
        field: 'Under 5 Years',
        name: 'Under 5 Years'
      },
      {
        field: '5 to 13 Years',
        name: '5 to 13 Years'
      },
      {
        field: '14 to 17 Years',
        name: '14 to 17 Years'
      },
      {
        field: '18 to 24 Years',
        name: '18 to 24 Years'
      },
      {
        field: '25 to 44 Years',
        name: '25 to 44 Years'
      },
      {
        field: '45 to 64 Years',
        name: '45 to 64 Years'
      },
      {
        field: '65 Years and Over',
        name: '65 Years and Over'
      },

    ],
    // x axis accessor
    x = function(d) {
      return d.State;
    },
    xOrient = 'bottom',
    xTickOrient = 'bottom',
    // set your ordinal domain
    xDomain = generalChartData.map(function(d) { return d.State; }),
    // set xRangeRoundBands
    xRangeRoundBands = {interval: [0, width - margins.left - margins.right], padding: .1},
    // set x scale: ordinal scale
    xScale = 'ordinal',
    xAxisClassName = 'x-axis',
    xLabel = "Age",
    xLabelPosition = 'bottom',
    xTickPadding = 3,
    xInnerTickSize = 6,
    xOuterTickSize = 6,
    // y axis accessor
    y = function(d) {
      return +d;
    },
    yOrient = 'left',
    yTickOrient = 'left',
    yRange = [height - margins.top - margins.bottom, 0],
    // y axis domain, set your min and max.
    yDomain = [0, d3.max(generalChartData, function(d) { return d.total; })],
    yScale = 'linear',
    yAxisClassName = 'y-axis',
    yLabel = "Population",
    // y tick format
    yTickFormat = d3.format(".2s"),
    yLabelPosition = 'left',
    yTickPadding = 4,
    yInnerTickSize = 6,
    yOuterTickSize = 6


  React.render(
    <BarStackZoom
      title= {title}
      data= {generalChartData}
      width= {width}
      height= {height}
      id= {id}
      margins= {margins}
      svgClassName= {svgClassName}
      titleClassName= {titleClassName}
      yAxisClassName= {yAxisClassName}
      xAxisClassName= {xAxisClassName}
      legendClassName= {legendClassName}
      legendPosition= {legendPosition}
      categoricalColors= {d3.scale.category10()}
      chartSeries = {chartSeries}
      showLegend= {showLegend}
      showXAxis= {showXAxis}
      showYAxis= {showYAxis}
      x= {x}
      showXGrid= {showXGrid}
      xDomain= {xDomain}
      xRangeRoundBands= {xRangeRoundBands}
      xScale= {xScale}
      xOrient= {xOrient}
      xTickOrient= {xTickOrient}
      xTickPadding = {xTickPadding}
      xInnerTickSize = {xInnerTickSize}
      xOuterTickSize = {xOuterTickSize}
      xLabel = {xLabel}
      xLabelPosition = {xLabelPosition}
      y= {y}
      showYGrid= {showYGrid}
      yOrient= {yOrient}
      yRange= {yRange}
      yDomain= {yDomain}
      yScale= {yScale}
      yTickOrient= {yTickOrient}
      yTickPadding = {yTickPadding}
      yInnerTickSize = {yInnerTickSize}
      yOuterTickSize = {yOuterTickSize}
      yTickFormat= {yTickFormat}
      yLabel = {yLabel}
      yLabelPosition = {yLabelPosition}
    />
  , document.getElementById('data_zoom_bar_stack')
  )
})()
```


<a href="/docs/zoom">
  <button type="button" class="btn btn-danger btn-lg">See more Charts with Zoom!</button>
</a>
