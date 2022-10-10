<script>

import * as d3 from "d3";
export default {
  mounted() {
    const width = 300;
    const height = 250;
    const data = [
      { displacement: 0, purpleHeight: 100, redHeight: 100, greenHeight: 100, blueHeight: 100 , blackHeight: 100  },
      { displacement: 100, purpleHeight: 10, redHeight: 20, greenHeight: 30, blueHeight: 40 , blackHeight: 50  },
    ];

    const svg = d3.select("#j-multiple-line-chart-two-svg").attr("width", width).attr("height", height);
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
              return d.purpleHeight;
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
        .rangeRound([30, width - 40]);

    const lineY = d3
        .scaleLinear()
        .domain(
            d3.extent(data, function (d) {
              return d.purpleHeight;
            })
        )
        .rangeRound([height - 60, 20]);
    //4. Creating a Line
    const firstLine = d3
        .line()
        .x(function (d) {
          return lineX(d.displacement);
        })
        .y(function (d) {
          return lineY(d.purpleHeight);
        });

    const secondLine = d3
        .line()
        .x(function (d) {
          return lineX(d.displacement);
        })
        .y(function (d) {
          return lineY(d.redHeight);
        });

    const thirdLine = d3
        .line()
        .x(function (d) {
          return lineX(d.displacement);
        })
        .y(function (d) {
          return lineY(d.greenHeight);
        });
    const fourthLine = d3
        .line()
        .x(function (d) {
          return lineX(d.displacement);
        })
        .y(function (d) {
          return lineY(d.blueHeight);
        });
    const fifthLine = d3
        .line()
        .x(function (d) {
          return lineX(d.displacement);
        })
        .y(function (d) {
          return lineY(d.blackHeight);
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
        .attr("stroke", "purple")
        .attr("stroke-width", 1.5)
        .attr("d", firstLine);
    g.append("path")
        .datum(data)
        .attr("fill", "none")
        .attr("stroke", "red")
        .attr("stroke-width", 1.5)
        .attr("d", secondLine);
    g.append("path")
        .datum(data)
        .attr("fill", "none")
        .attr("stroke", "green")
        .attr("stroke-width", 1.5)
        .attr("d", thirdLine);
    g.append("path")
        .datum(data)
        .attr("fill", "none")
        .attr("stroke", "blue")
        .attr("stroke-width", 1.5)
        .attr("d", fourthLine);
    g.append("path")
        .datum(data)
        .attr("fill", "none")
        .attr("stroke", "black")
        .attr("stroke-width", 1.5)
        .attr("d", fifthLine);
  },
};
</script>

<template>
  <div>
    <svg id="j-multiple-line-chart-two-svg"></svg>
  </div>
</template>

<style scoped>

</style>
