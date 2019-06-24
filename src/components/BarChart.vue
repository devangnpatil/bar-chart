<template>
    <div class='graph-wrapper'>
        <h2>Bar Chart</h2>
        <canvas id="myCanvas" width="1000" height="500"></canvas>
    </div>
    
</template>
<script>
        
export default {
    props: ['chartData'],
    data(){
        return{
            data: []
        }
    },
    name: 'barChart',
    methods:{
		drawGrid: function(ctx, xGrid, yGrid, canvas, cellSize) {

			ctx.beginPath();
			while (xGrid < canvas.height) {
				ctx.moveTo(0, xGrid);
				ctx.lineTo(canvas.width, xGrid)
				xGrid += cellSize;
			}

			while (yGrid < canvas.width) {
				ctx.moveTo(yGrid, 0);
				ctx.lineTo(yGrid, canvas.height)
				yGrid += cellSize;
			}
			ctx.strokeStyle = "grey";
			ctx.stroke();
        },
        
		blocks: function (count) {
			return count * 10;
        },

		drawAxis: function (ctx) {
			let yPlot = 48;
			let pop = 0;
			ctx.beginPath();
			ctx.strokeStyle = "black";
			ctx.moveTo(this.blocks(5), this.blocks(5));
			ctx.lineTo(this.blocks(5), this.blocks(48));
			ctx.lineTo(this.blocks(80), this.blocks(48));

			ctx.moveTo(this.blocks(5), this.blocks(40));
			ctx.stroke();
			for (let i = 0; i <= 10; i++) {
				ctx.strokeText(pop, this.blocks(2), this.blocks(yPlot));
				yPlot -= 5;
				pop += 500;
			}
		},

		drawChart: function (ctx, canvas) {
			var width = 40;
			ctx.beginPath();
			ctx.strokeStyle = 'black';
			ctx.moveTo(this.blocks(5), this.blocks(48));
			var xPlot = 10;
			this.chartData.forEach(element => {
				var cHeight = 40 //canvas.height / 100
				ctx.fillStyle = element.color;
				ctx.strokeText(element.name, this.blocks(xPlot+1), 495);
				ctx.fillRect(this.blocks(xPlot), 480, width, this.blocks((canvas.height-element.value)/100)-this.blocks(5));
				xPlot += 5;

			});
			ctx.stroke();

		}
    },
    computed:{

    },

    mounted(){
        let canvas = document.getElementById('myCanvas');
        let xGrid = 10;
        let yGrid = 10;
        let cellSize = 10;
        let ctx = canvas.getContext('2d');

		this.drawGrid(ctx, xGrid, yGrid, canvas, cellSize);
		this.drawAxis(ctx);
		this.drawChart(ctx, canvas);
    }

}
</script>
<style scoped>
    * {
        margin: 0;
        padding: 0;
    }

    body {
        margin: 50px auto;
        text-align: center;
    }

    canvas {
        border: 1px solid black;
    }

    .graph-wrapper h2{
        text-align: center;
        padding: 15px;
    }
    .graph-wrapper{
        margin: 0 auto;
        text-align:  center;
    }
</style>
