Chart Component:

<div id="blank-container" class="demo"></div>
<script src="/react-d3-example/dist/min/es5/chart.min.js"></script>

```js
var React = require('react');
var Chart = require('react-d3-core').Chart;

// Example
(function() {

  var width = 500,
    height = 400,
    margins = {top: 20, right: 50, bottom: 20, left: 50},
    id = "test-chart",
    svgClassName = "test-chart-class",
    titleClassName = "test-chart-title-class";

  // chart title
  var title = "test chart lib";
  var style = {
    fill: 'red'
  };

  React.render(
    <Chart
      title= {title}
      width= {width}
      height= {height}
      margins= {margins}
      id= {id}
      svgClassName= {svgClassName}
      titleClassName= {titleClassName}>
      <rect style={style} width="100%" height="100%"/>
    </Chart>
  , document.getElementById('blank-container'))

})()
```
