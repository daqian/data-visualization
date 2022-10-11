<script>

import * as d3 from "d3";
export default {
  mounted() {
    const width = 300;
    const height = 250;
    const data = [
      { dataY: 0, purpleX: 76, redX: 70, greenX: 64, blueX: 58 , blackX: 52 },
      { dataY: 6, purpleX: 76, redX: 70, greenX: 64, blueX: 58 , blackX: 52 },
      { dataY: 12, purpleX: 76, redX: 70, greenX: 64, blueX: 58 , blackX: 52  },
      { dataY: 18, purpleX: 76, redX: 70, greenX: 64, blueX: 58 , blackX: 52  },
      { dataY: 18, purpleX: 69, redX: 63, greenX: 57, blueX: 51 , blackX: 45  },
      { dataY: 18, purpleX: 69, redX: 63, greenX: 57, blueX: 51 , blackX: 45  },
      { dataY: 30, purpleX: 69, redX: 63, greenX: 57, blueX: 51 , blackX: 45  },
      { dataY: 30, purpleX: 63, redX: 57, greenX: 51, blueX: 45 , blackX: 39  },
      { dataY: 74, purpleX: 63, redX: 57, greenX: 51, blueX: 45 , blackX: 39  },
      { dataY: 82, purpleX: 63, redX: 57, greenX: 51, blueX: 45 , blackX: 39  },
      { dataY: 82, purpleX: 55, redX: 49, greenX: 43, blueX: 37 , blackX: 31  },
      { dataY: 82, purpleX: 51, redX: 45, greenX: 39, blueX: 33 , blackX: 27  },
      { dataY: 94, purpleX: 51, redX: 45, greenX: 39, blueX: 33 , blackX: 27  },
      { dataY: 94, purpleX: 39, redX: 33, greenX: 27, blueX: 21 , blackX: 15  },
      { dataY: 94, purpleX: 35, redX: 29, greenX: 23, blueX: 17 , blackX: 11  },
      { dataY: 100, purpleX: 35, redX: 29, greenX: 23, blueX: 17 , blackX: 11 },
    ];

    const svg = d3.select("#j-multiple-line-chart-two-svg").attr("width", width).attr("height", height);
    const g = svg.append("g");


    //3. Creating the Chart Axes
    const x = d3
        .scaleTime()
        .domain(
            d3.extent(data, function (d) {
              return d.purpleX;
            })
        )
        .rangeRound([0, width - 60]);

    const y = d3
        .scaleLinear()
        .domain(
            d3.extent(data, function (d) {
              return d.dataY;
            })
        )
        .rangeRound([height - 60, 0]);

    const lineX = d3
        .scaleTime()
        .domain(
            d3.extent(data, function (d) {
              return d.purpleX;
            })
        )
        .rangeRound([30, width - 40]);

    const lineY = d3
        .scaleLinear()
        .domain(
            d3.extent(data, function (d) {
              return d.dataY;
            })
        )
        .rangeRound([height - 60, 20]);
    //4. Creating a Line
    const firstLine = d3
        .line()
        .x(function (d) {
          return lineX(d.purpleX);
        })
        .y(function (d) {
          return lineY(d.dataY);
        });

    const secondLine = d3
        .line()
        .x(function (d) {
          return lineX(d.redX);
        })
        .y(function (d) {
          return lineY(d.dataY);
        });

    const thirdLine = d3
        .line()
        .x(function (d) {
          return lineX(d.greenX);
        })
        .y(function (d) {
          return lineY(d.dataY);
        });
    const fourthLine = d3
        .line()
        .x(function (d) {
          return lineX(d.blueX);
        })
        .y(function (d) {
          return lineY(d.dataY);
        });
    const fifthLine = d3
        .line()
        .x(function (d) {
          return lineX(d.blackX);
        })
        .y(function (d) {
          return lineY(d.dataY);
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
