<script>

import * as d3 from "d3";
export default {
  mounted() {
    const width = 300;
       const height = 250;
      const margin = {left:50,top:30,right:20,bottom:20};
// 图表的宽度=svg的宽度减去margin
       const g_width = width - margin.left-margin.right;
        const g_height = height - margin.top - margin.bottom;
    const svg = d3.select("#j-curve-chart-svg").attr("width", width).attr("height", height);


    const g = svg.append("g")
        // 设置x,y轴偏移量
        .attr("transform","translate(" +margin.left+","+ margin.top +")")

    const data = [1,3,5,7,8,4,3,7]

// 设置缩放
    const scale_x = d3.scaleLinear().domain([0,data.length-1]).range([0,g_width])
    const scale_y = d3.scaleLinear().domain([0,d3.max(data)]).range([g_height,0])

    const line_generator = d3.line()
        // d表示传进来的数据 i表示数据的下标
        .x(function(d,i){return scale_x(i);}) // 0,1,2,3
        .y(function(d){return scale_y(d);}); // 1,3,5
        // 去除线的棱角 使其顺滑
        // .interpolate("cardinal")

    g.append("path")
        // d 是 path data的缩写 将data数据传人
        .attr("d",line_generator(data)) // d = "M1,0L20,40L40,50L100,100L0,200"
    const x = d3
        .scaleTime()
        .domain(
            d3.extent(data, function (d) {
              return d;
            })
        )
        .rangeRound([0, width]);

    const y = d3
        .scaleLinear()
        .domain(
            d3.extent(data, function (d) {
              return d.amount;
            })
        )
        .rangeRound([height, 0]);

    //4. Creating a Line
    const line = d3
        .line()
        .x(function (d) {
          return x(parseTime(d.date));
        })
        .y(function (d) {
          return y(d.amount);
        });

    g.append("g")
        .attr("transform", "translate(0," + height + ")")
        .call(d3.axisBottom(x));

    g.append("g")
        .call(d3.axisLeft(y))
        .append("text")
        .attr("fill", "#000")
        .attr("transform", "rotate(-90)")
        .attr("y", 6)
        .attr("dy", "0.71em")
        .attr("text-anchor", "end")
        .text("Price ($)");

  },
};
</script>

<template>
  <div>
    <svg id="j-curve-chart-svg"></svg>
  </div>
</template>

<style scoped>

</style>
