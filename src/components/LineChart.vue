<script>

import * as d3 from "d3";
export default {
  mounted() {
    const width = 300;
    const height = 250;
    const data = [
      { displacement: 0.5, height: 1.8 },
      { displacement: 1, height: 0 },
      { displacement: 1.5, height: 0 },
      { displacement: 2, height: 0 },
      { displacement: 2.5, height: 0 },
      { displacement: 3, height: 0 },
    ];

    const svg = d3.select("#j-line-chart-svg").attr("width", width).attr("height", height);
    const g = svg.append("g");


    //3. Creating the Chart Axes
    const x = d3
        .scaleTime()
        .domain(
            d3.extent(data, function (d) {
              return d.displacement;
            })
        )
        .rangeRound([0, width - 60]);

    const y = d3
        .scaleLinear()
        .domain(
            d3.extent(data, function (d) {
              return d.height;
            })
        )
        .rangeRound([height - 60, 0]);

    const lineX = d3
        .scaleTime()
        .domain(
            d3.extent(data, function (d) {
              return d.displacement;
            })
        )
        .rangeRound([0, width - 40]);

    const lineY = d3
        .scaleLinear()
        .domain(
            d3.extent(data, function (d) {
              return d.height;
            })
        )
        .rangeRound([height - 40, 20]);
    //4. Creating a Line
    const line = d3
        .line()
        .x(function (d) {
          return lineX(d.displacement);
        })
        .y(function (d) {
          return lineY(d.height);
        });

    //5. Appending the Axes to the Chart
    g.append("g")
        .attr("transform", "translate(30," + (height - 40) + ")")
        .call(d3.axisBottom(x))
        .append("text")
        .attr("fill", "#000")
        // .attr("x", 6)
        .attr("dx", width - 40)
        .attr("dy", "-0.71em")
        .attr("text-anchor", "end")
        .text("排量(L/S)");

    g.append("g")
        .attr("transform", "translate(30, 20)")
        .call(d3.axisLeft(y))
        .append("text")
        .attr("fill", "#000")
        // .attr("transform", "rotate(-90)")
        .attr("y", -18)
        // .attr("dx", "0.71em")
        .attr("dy", "0.71em")
        .attr("text-anchor", "middle")
        .text("高度(cm)");

    //6. Appending a path to the Chart
    g.append("path")
        .datum(data)
        .attr("fill", "none")
        .attr("stroke", "red")
        .attr("stroke-width", 1.5)
        .attr("d", line);
    svg.append("g")
        .attr("fill", "none")
        .attr("stroke", "red")
        .attr("stroke-width", 2)
        .selectAll("circle")
        .data(data)
        .join("circle")
        .attr("cx", function (d) {
          return lineX(d.displacement);
        })
        .attr("cy", function (d) {
          return lineY(d.height);
        })
        .attr("r", 2);
  },
};
</script>

<template>
  <div>
    <svg id="j-line-chart-svg"></svg>
  </div>
</template>

<style scoped>

</style>
