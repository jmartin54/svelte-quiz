<script lang="ts">
  import { onMount } from "svelte";
  import Space from "../lib/Space.svelte";
  import PageLayout from "./PageLayout.svelte";

    let canvas;
    onMount(()=>{

        // square the canvas
        let min = Math.min(window.innerWidth, window.innerHeight);
        canvas.width = min * 0.5;
        canvas.height = min * 0.5;

        let context = canvas.getContext('2d');
        
        let tau = 2 * Math.PI;
        let cx = canvas.width / 2;
        let cy = canvas.height / 2;

        // sin wave at center
        // for(let x = 0; x < canvas.width; x ++) {
        //     const ystart =  canvas.height / 2;
        //     if(x == 0) context.moveTo(0,ystart);
        //     else context.lineTo(x, 10.*Math.sin(x / 10.) + ystart);
        // }

        // tangent line-circle at center
        // for(let s = 0; s < 100; s++) {
        //     let a = 80.;
        //     if(s == 0) context.moveTo(cx + a*Math.sin(s), cy + a*Math.cos(s))
        //     else context.lineTo(cx +a* Math.sin(s), cy + a*Math.cos(s))
        // }

        // simple circle at center
        // for(let s = 0; s < 100; s++) {
        //     let a = Math.min(cx, cy) * 0.9;
        //     let step = 0.1 * s;
        //     if(s == 0)  context.moveTo(cx + a*Math.sin(step), cy + a*Math.cos(step))
        //     else context.lineTo(cx + a*Math.sin(step), cy + a*Math.cos(step))
        // }

        function polar(deg, mag) {
            return {
                x: cx + mag * Math.sin(deg * tau / 360),
                y: cx + mag * Math.cos(deg * tau / 360),
            }
        }

        // polar circle
        // for(let i = 0; i <= 360; i++) {
        //     const point = polar(i, 40.);
        //     if(i == 0) context.moveTo(point.x, point.y)
        //     else context.lineTo(point.x, point.y)
        // }

        // star of david
        // const mag = Math.min(cx, cy) * 0.9
        // {
        //     let coords = [polar(0, mag), polar(120, mag), polar(240, mag)];
        //     let last = coords[coords.length - 1];
        //     context.moveTo(last.x, last.y)
        //     for(var i in coords) {
        //         context.lineTo(coords[i].x, coords[i].y)
        //     }
        // }
        // {
        //     let coords = [polar(60, mag), polar(180, mag), polar(300, mag)];
        //     let last = coords[coords.length - 1];
        //     context.moveTo(last.x, last.y)
        //     for(var i in coords) {
        //         context.lineTo(coords[i].x, coords[i].y)
        //     }
        // }

        // hexagon
        // const mag = Math.min(cx, cy) * 0.9
        // let coords = [polar(0, mag), polar(60, mag), polar(120, mag), polar(180, mag), polar(240, mag), polar(300, mag), polar(360, mag)];
        // let last = coords[coords.length - 1];
        // context.moveTo(last.x, last.y);
        // for(var coord of coords) context.lineTo(coord.x, coord.y)
        

        // hexagon from triangles
        // const mag = Math.min(cx, cy) * 0.9
        // for(let d = 0; d <= 360; d += 60) {
        //     const a = polar(d, mag);
        //     const b = polar(d + 60, mag);
        //     context.lineTo(a.x, a.y)
        //     context.lineTo(b.x, b.y)
        //     context.lineTo(cx, cy)
        // }

        // stroke the examples above 
        // context.stroke();


        // colored hexagon
        // const mag = Math.min(cx, cy) * 0.9
        // let points = [
        //     {start: 0,   end: 60,  color: '#f00'},
        //     {start: 60,  end: 120, color: '#0f0'},
        //     {start: 120, end: 180, color: '#00f'},
        //     {start: 180, end: 240, color: '#ff0'},
        //     {start: 240, end: 300, color: '#f0f'},
        //     {start: 300, end: 360, color: '#0ff'},
        // ]
        // for(var point of points) {
        //     const a = polar(point.start, mag);
        //     const b = polar(point.end, mag);
        //     context.beginPath()
        //     context.fillStyle = point.color;
        //     context.lineTo(a.x, a.y)
        //     context.lineTo(b.x, b.y)
        //     context.lineTo(cx, cy)
        //     context.closePath();
        //     context.fill();
        // }


        const mag = Math.min(cx, cy) * 0.9
        let points = [
            {angle: 0,   color: '#f0f'},
            {angle: 60,  color: '#00f'},
            {angle: 120, color: '#0f0'},
            {angle: 180, color: '#ff0'},
            {angle: 240, color: '#f80'},
            {angle: 300, color: '#f00'},
        ]
        for(var point of points) {
            const a = polar(point.angle - 30, mag* 0.7);
            const b = polar(point.angle, mag);
            const c = polar(point.angle + 30, mag* 0.7);
            context.beginPath()
            context.fillStyle = point.color;
            context.lineTo(a.x, a.y)
            context.lineTo(b.x, b.y)
            context.lineTo(c.x, c.y)
            context.lineTo(cx, cy)
            context.closePath();
            context.fill();
        }

    })
</script>

<PageLayout on:click>
    <h1>Hello World</h1>

    <div class="container">
        <canvas bind:this={canvas}></canvas>
    </div>
    <Space />
</PageLayout>

<style>
    .container {
        text-align: center;
    }
</style>