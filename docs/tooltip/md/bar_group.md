Bar Group Tooltip:

<div id="data_bar_group" class="demo"></div>
<script src="/react-d3-example/dist/min/es5/bar_group_tooltip.min.js"></script>

```js
"use strict";

var React = require('react');
var BarGroupTooltip = require('react-d3-tooltip').BarGroupTooltip;

(function() {
  var generalChartData = require('dsv?delimiter=,!../data/age.csv')

  var ageNames = d3.keys(generalChartData[0]).filter(function(key) { return key !== "State"; });

  generalChartData.forEach(function(d) {
    d.ages = ageNames.map(function(name) { return {name: name, value: +d[name]}; });
  });

  var width = 700,
    height = 400,
    margins = {top: 50, right: 50, bottom: 50, left: 50},
    id = "test-chart",
    title = "Bar Group Chart",
    svgClassName = "test-chart-class",
    titleClassName = "test-chart-title-class",
    legendClassName = "test-legend",
    legendPosition = 'right',
    labelOffset = 30,

    showLegend = true,
    showXAxis = true,
    showYAxis = true,
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
    x = function(d) {
      return d.State;
    },
    xOrient = 'bottom',
    xTickOrient = 'bottom',
    xDomain = generalChartData.map(function(d) { return d.State; }),
    xRangeRoundBands = {interval: [0, width - margins.left - margins.right], padding: .1},
    xScale = 'ordinal',
    xAxisClassName = 'x-axis',
    xLabel = "Age",
    xLabelPosition = 'bottom',
    y = function(d) {
      return +d;
    },
    yOrient = 'left',
    yTickOrient = 'right',
    yRange = [height - margins.top - margins.bottom, 0],
    yDomain = [0, d3.max(generalChartData, function(d) { return d3.max(d.ages, function(d) { return d.value; }); })],
    yScale = 'linear',
    yAxisClassName = 'y-axis',
    yLabel = "Population",
    yTickFormat = d3.format(".2s"),
    yLabelPosition = 'left',
    categoricalColors = d3.scale.category10();


  React.render(
      <BarGroupTooltip
        title= {title}
        data= {generalChartData}
        width= {width}
        height= {height}
        id= {id}
        margins= {margins}
        svgClassName= {svgClassName}
        labelOffset = {labelOffset}
        titleClassName= {titleClassName}
        yAxisClassName= {yAxisClassName}
        xAxisClassName= {xAxisClassName}
        legendClassName= {legendClassName}
        legendPosition= {legendPosition}
        categoricalColors= {categoricalColors}
        chartSeries = {chartSeries}
        showLegend= {showLegend}
        showXAxis= {showXAxis}
        showYAxis= {showYAxis}
        x= {x}
        xDomain= {xDomain}
        xRangeRoundBands= {xRangeRoundBands}
        xScale= {xScale}
        xOrient= {xOrient}
        xTickOrient= {xTickOrient}
        xLabel = {xLabel}
        xLabelPosition = {xLabelPosition}
        y= {y}
        yOrient= {yOrient}
        yRange= {yRange}
        yDomain= {yDomain}
        yScale= {yScale}
        yTickOrient= {yTickOrient}
        yTickFormat= {yTickFormat}
        yLabel = {yLabel}
        yLabelPosition = {yLabelPosition}
      />
  , document.getElementById('data_bar_group')
  )
})()
```
