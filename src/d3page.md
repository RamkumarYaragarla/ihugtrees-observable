#   Our D3 Visualizations

Check out our main d3.js dataset visualizations at site: [I Hug Trees](https://ihugtrees.org/data-analytics/co2-emissions-by-country.html)

<div id="chart"></div>

<script src="https://d3js.org/d3.v7.min.js"></script>
<script>
const data = [25, 40, 30, 55, 20, 60, 45];
const width = 600, height = 300;

const svg = d3.select("#chart")
  .append("svg")
  .attr("width", width)
  .attr("height", height);

const x = d3.scaleBand().domain(data.map((d,i)=>i)).range([0,width]).padding(0.2);
const y = d3.scaleLinear().domain([0,d3.max(data)]).range([height,0]);

svg.selectAll(".bar")
  .data(data)
  .enter().append("rect")
  .attr("class","bar")
  .attr("x",(d,i)=>x(i))
  .attr("y",d=>y(d))
  .attr("width",x.bandwidth())
  .attr("height",d=>height-y(d))
  .attr("fill","#336699");

svg.append("g").attr("transform",`translate(0,${height})`).call(d3.axisBottom(x));
svg.append("g").call(d3.axisLeft(y));
</script>
Also our analytics site where we have other d3.js visualizations: [Green cover data analytics ](https://ihugtrees.org/data-analytics.html)
