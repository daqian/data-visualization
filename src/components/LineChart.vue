<script>

import * as d3 from "d3";
export default {
  mounted() {
    const width = 300;
    const height = 250;
    const data = [
      { displacement: 0.5, redHeight: 1.6, blueHeight: 1.0 },
      { displacement: 1, redHeight: 0, blueHeight: 1.6 },
      { displacement: 1.5, redHeight: 0, blueHeight: 1.1 },
      { displacement: 2, redHeight: 0, blueHeight: 0.9 },
      { displacement: 2.5, redHeight: 0, blueHeight: 0.8 },
      { displacement: 3, redHeight: 0, blueHeight: 0.7 },
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
              return d.redHeight;
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
              return d.redHeight;
            })
        )
        .rangeRound([height - 40, 20]);
    //4. Creating a Line
    const firstLine = d3
        .line()
        .x(function (d) {
          return lineX(d.displacement);
        })
        .y(function (d) {
          return lineY(d.redHeight);
        });

    const secondLine = d3
        .line()
        .x(function (d) {
          return lineX(d.displacement);
        })
        .y(function (d) {
          return lineY(d.blueHeight);
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
        .attr("d", firstLine);
    g.append("path")
        .datum(data)
        .attr("fill", "none")
        .attr("stroke", "blue")
        .attr("stroke-width", 1.5)
        .attr("d", secondLine);
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
          return lineY(d.redHeight);
        })
        .attr("r", 2);
    svg.append("g")
        .attr("fill", "none")
        .attr("stroke", "blue")
        .attr("stroke-width", 2)
        .selectAll("circle")
        .data(data)
        .join("circle")
        .attr("cx", function (d) {
          return lineX(d.displacement);
        })
        .attr("cy", function (d) {
          return lineY(d.blueHeight);
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
