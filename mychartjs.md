Before you may use chartJs, you have to build it or you can use the built dist from the github repo (We'd use latter approach)
chartJs: https://www.chartjs.org/
github: https://github.com/chartjs/Chart.js

you can also use the cdn, look it up from the docs
download the js and css here - dist directory
They deserve a star or something that can push them
https://github.com/chartjs/Chart.js/tree/v2.8.0
I will save mine as chart.js and chart.css

create an index file
include the script tag for the chart.js (path to chart.js)
<script src="chart.js"></script>

the css, <link rel="stylesheet" href="chart.css">


create a canvas object in the body tag
<canvas id="myChart" width="300" height="200"></canvas>

create an instance of the Chart
var myChart = new Chart(ctx, {})

the {} is an object. basically the object is made up of the type of chart, the data and some options. These are comma seperated

the types of chart (line, bar, radar, doughnut, pie, polarArea, bubble, scatter)
Eg: type:'bar'

the data is an array of objects of (labels, datasets (label, data, backgroundColor, borderColor, borderWidth))

Eg:
data: {
	labels: ['team A', 'team B', 'team C', 'team D', 'team E'],
	dataset: [{
		label: 'This is the title for this particular data',
		data: [9,8,5,4,7],
		backgroundColor: [
			'rgba(255, 99, 132, 0.2)',
            'rgba(54, 162, 235, 0.2)',
            'rgba(255, 206, 86, 0.2)',
            'rgba(75, 192, 192, 0.2)',
            'rgba(153, 102, 255, 0.2)'
        ],
        borderColor: [
            'rgba(255, 99, 132, 1)',
            'rgba(54, 162, 235, 1)',
            'rgba(255, 206, 86, 1)',
            'rgba(75, 192, 192, 1)',
            'rgba(153, 102, 255, 1)'
        ],
        borderWidth: 1
	}]
}

Notice the keys, labels and label. Labels is in the data object and this is like the component names on the x-axis but the label is in the dataset array which belongs to a particular object/element in the array. This label is the title of the current data

for the options we can simply do;
options: {
        scales: {
            yAxes: [{
                ticks: {
                    beginAtZero: true
                }
            }]
        }
    }
    
this is basically saying that the yAxes should begin from zero

After everything, we should a similar content in the index.html file as the code below

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="mechartjs/Chart.min.css">
    <title>Document</title>
</head>

<body>
    <h1>Chart JS</h1>
    <!-- <div style="width: 350px; height: 250px;"> -->
    <canvas id="myChart" width="300" height="200"></canvas>
    <!-- </div> -->

    <script src="mechartjs/Chart.min.js"></script>

    <script>
        var ctx = document.getElementById('myChart');
            var myChart = new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: ['Sindel', 'John', 'Nate', 'Gloria', 'Pearl'],
                    datasets: [{
                        label: 'A bar chart of the scores of 5 students',
                        data: [17, 19, 13, 15, 12, 13],
                        backgroundColor: [
                            'rgba(255, 99, 132, 0.2)',
                            'rgba(54, 162, 235, 0.2)',
                            'rgba(255, 206, 86, 0.2)',
                            'rgba(75, 192, 192, 0.2)',
                            'rgba(153, 102, 255, 0.2)'
                        ],
                        borderColor: [
                            'rgba(255, 99, 132, 1)',
                            'rgba(54, 162, 235, 1)',
                            'rgba(255, 206, 86, 1)',
                            'rgba(75, 192, 192, 1)',
                            'rgba(153, 102, 255, 1)'
                        ],
                        borderWidth: 1
                    }
    },
                options: {
                    scales: {
                        yAxes: [{
                            ticks: {
                                beginAtZero: true
                            }
                        }]
                    }
                }
            });
    </script>


</body>

</html>
```


try to chnage the type and look at how the graph changes
