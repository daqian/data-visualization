<script>

import * as d3 from "d3";
export default {
  mounted() {
    const width = 300;
    const height = 250;
    const data = [
      { dataY: 0, purpleX: 100, redX: 100, greenX: 100, blueX: 100 , blackX: 100  },
      { dataY: 0, purpleX: 90, redX: 100, greenX: 100, blueX: 100 , blackX: 100  },
      { dataY: 0, purpleX: 80, redX: 100, greenX: 100, blueX: 100 , blackX: 100  },
      { dataY: 0, purpleX: 70, redX: 100, greenX: 100, blueX: 100 , blackX: 100  },
      { dataY: 0, purpleX: 60, redX: 100, greenX: 100, blueX: 100 , blackX: 100  },
      { dataY: 10, purpleX: 60, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 20, purpleX: 60, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 30, purpleX: 60, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 40, purpleX: 60, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 40, purpleX: 50, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 40, purpleX: 40, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 40, purpleX: 30, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 40, purpleX: 20, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 40, purpleX: 20, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 50, purpleX: 20, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 50, purpleX: 10, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 50, purpleX: 9, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 50, purpleX: 8, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 50, purpleX: 7, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 60, purpleX: 7, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 70, purpleX: 7, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 80, purpleX: 7, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 90, purpleX: 7, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
      { dataY: 100, purpleX: 7, redX: 20, greenX: 30, blueX: 40 , blackX: 50  },
    ];

    const svg = d3.select("#j-multiple-line-chart-one-svg").attr("width", width).attr("height", height);
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
    <svg id="j-multiple-line-chart-one-svg"></svg>
  </div>
</template>

<style scoped>

</style>
