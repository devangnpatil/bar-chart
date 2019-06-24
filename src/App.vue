<template>
  <div id="app">
    <BarChart :chartData="barChartData"></BarChart>
  </div>
</template>

<script>
import BarChart from './components/BarChart'
export default {
  name: 'app',
  components: {
    BarChart
  },

  data () {
    return {
      barChartData: [
        // {name:"Rohit", value:149, color:"#DC143C"},
        // {name:"Rahul", value:178, color:"#FF8C00"},
        // {name:"Virat", value:120, color:"#90EE90"},
        // {name:"Hardik", value:30, color:"#20B2AA"},
        // {name:"Dhoni", value:25, color:"#87CEFA"},
        // {name:"Jadhav", value:35, color:"#FFB6C1"},
        // {name:"Vijay", value:19, color:"#FAFAD2"},
        // {name:"M. Shami", value:7, color:"#FFDAB9"},
        // {name:"Kuldeep", value:0, color:"#778899"},
        // {name:"Chahal", value:13, color:"#808080"},
        // {name:"Bumrah", value:0, color:"#FFE4E1"}
          {name: 'Aus', value:1000, color:'red'},
          {name: 'India', value:2000, color:'blue'},
          {name: 'China', value:3000, color:'green'},
          {name: 'USA', value:2000, color:'grey'},
          {name: 'UK', value:500, color:'pink'}
      ]
    }
  }
}
</script>

<style>
html, body {
  margin: 0;
  padding: 0;
}
*{
  box-sizing: border-box;
}
</style>
