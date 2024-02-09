<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Smiley Face Clustering</title>
    <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
    <script id="MathJax-script" async src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML"></script>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            line-height: 1.6;
            color: #333;
        }
        .container {
            max-width: 800px;
            margin: auto;
            overflow: hidden;
            padding: 0 20px;
        }
        .header, .footer {
            background: #007bff;
            color: #ffffff;
            padding: 20px 0;
            text-align: center;
        }
        h1, h2, h3 {
            margin: 20px 0;
        }
        p {
            margin: 10px 0;
        }
        .plot-container {
            text-align: center;
            margin: 20px 0;
        }
        button {
            background: #333;
            color: #ffffff;
            border: none;
            padding: 10px 20px;
            margin: 20px 0;
            cursor: pointer;
        }
        button:hover {
            opacity: 0.9;
        }
    </style>
</head>
<body>

<div class="header">
    <div class="container">
        <h1>Interactive Smiley Face Clustering: A Baby Project</h1>
    </div>
</div>

<div class="container">
    <p>This interactive demonstration shows how a simple form of clustering can be visualized. Initially, a smiley face is plotted using predetermined data points. By clicking the "Cluster" button, the data points are re-colored based on their proximity to predefined centroids, simulating a basic clustering process.</p>
    
    <div class="plot-container">
        <div id="plot" style="width: 100%; max-width: 600px; margin: auto;"></div>
        <button onclick="startClustering()">Cluster</button>
    </div>

    <h2>How It Works</h2>
    <h3>Plotting Portion</h3>
    <p>The smiley face is generated using a JavaScript function that plots points in specific patterns to form a face, eyes, and a smile. For the face and eyes, we use the circle equation centered at x=4,5,6 and of radius 0.5, 3, 0.5, respectively. For the smile, we have used part of an ellipse having center at (5,3), major axis 2, and minor axis 1.</p>
    
    <h3>Coloring Portion</h3>
    <p>The clustering is simulated by assigning each point to the nearest of three centroids (4,7), (6,7), and (5,4). Here we chose the centroids by our own but there is a mathematical code behind it discussed in the next paragraph. Then we changed the color of the points who are close to these three centroids changing the point's color as red, green, and blue respectively.</p>
    
    <h3>Clustering Portion</h3>
    <p>Next, we clubbed all the points of the same color close to each other.</p>
</div>

<div class="container">
    <h2>
        What is K_Means?
    </h2>
    <p> K-Means is a technique that we use to cluster a group of data.

    <h3>Objective</h3>
        The goal of K-means clustering is to partition 
        n observations into k clusters in which each observation belongs to the cluster with the nearest mean, 
        serving as a prototype of the cluster.
        
    <h3>Steps and Math Involved</h3>
    <h4>Initialization:</h4>
        Choose k initial centroids (mean points) for the clusters. This can be done randomly or by using more sophisticated methods to help improve convergence and results.
        (In some portion we can start with random clusters as well, the results should be almost identical)
    <h4>Assignment Step:</h4>
        Assign each data point xi to the nearest centroid. The "nearest" is usually determined by the Euclidean distance, though other distances can be used depending on the context.
        The Euclidean distance between two points \(x\) and \(y\) in a plane is calculated as: \(d(x,y) = ||x - y||\). If \(x=(x_1,x_2)\) and \(y=(y_1,y_2)\) then 
        \(d(x,y) = \sqrt{(x_1-y_1)^2+(x_2-y_2)^2}\).
        In multidimensional space, this extends to:
        Update Step: \(d(\bar x, \bar y) = \sqrt{\sum_{i=1}^n(x_i-y_i)^2}\) where \(\bar x =(x_1,\cdots, x_n)\).
        
        After all points have been assigned to clusters, recalculate the centroids of each cluster as the mean of all points in the cluster.
        The new centroid of a cluster is calculated as: \(c_j:=\text{centriod}(x_j)=\frac 1{|S_j|} \sum_{x_i \in S_j} x_i \)
        
        Here, \(S_j\) represents the set of all points assigned to cluster \(j\) and \(|S_j|\) is the no of points in \(S_j\).

    <h4>Iteration:</h4>
        
        Repeat the assignment and update steps until the centroids no longer change significantly, indicating that the algorithm has converged, or until a specified number of iterations has been reached.
        Objective Function
 
    <h4>Objective Function:</h4>
        K-means aims to minimize the within-cluster sum of squares (WCSS), which is the sum of squared distances between each point and its centroid within a cluster. The objective function, also known as the cost function, to be minimized is:
        \(J=\sum_{j=1}^k\sum_{x_i \in S_j}||x_i-c_j||^2\).
        
    <h4>Challenges and Considerations</h4>
        Choosing k: Determining the optimal number of clusters \(k\) is a critical step and often not straightforward. Methods like the "elbow method" or the "silhouette score" can help in choosing k.
        Sensitivity to Initial Centroids: The final clusters can be significantly influenced by the initial choice of centroids. Multiple runs with different initializations or using methods like k-means++ can mitigate this issue.
        Convergence to Local Minima: K-means may converge to a local minimum of the cost function, which may not be the global minimum. Again, multiple runs and comparisons can help find better solutions.
        The K-means algorithm is a powerful tool for exploratory data analysis and pattern recognition, with applications ranging from image compression to market segmentation. Its simplicity and efficiency make it widely used, although it is essential to understand its limitations and the underlying mathematical principles to apply it effectively.</p>

    <h4>Reference</h4>
        <ul>
            <li>I want to thank my wife first as she gave me this idea of making some interactive notes. She saw it in some other portfolios of quant people. This is my first writing in html and Java. </li>
            <li>Being that said ChatGPT and Google made my life easier by telling me the syntax of html and Java.</li>
        </ul>

        Thanks a lot to all of you for reading this.
</div>

<div class="footer">
    <div class="container">
        <p>Project by [Arnab Dey Sarkar]. ©2023</p>
    </div>
</div>

<script>
    let clusteringStep = 0; // 0: Initial plot, 1: Color change, 2: Clustering
    // Function to plot the initial smiley face
    function generateSmileyFaceData() {
        let data = { x: [], y: [], mode: 'markers', type: 'scatter', marker: { color: 'blue' } };

        // Face
        for (let i = 0; i < 360; i += 3.6) {
            let rad = Math.PI / 180 * i;
            data.x.push(5 + 3 * Math.cos(rad));
            data.y.push(5 + 3 * Math.sin(rad));
        }

        // Eyes
        [4, 6].forEach(cx => {
            for (let i = 0; i < 360; i += 36) {
                let rad = Math.PI / 180 * i;
                data.x.push(cx + 0.5 * Math.cos(rad));
                data.y.push(6 + 0.5 * Math.sin(rad));
            }
        });

        // Smile
        for (let i = 45; i <= 135; i += 9) {
            let rad = Math.PI / 180 * i;
            data.x.push(5 + 2 * Math.cos(rad));
            data.y.push(3 + 1 * Math.sin(rad));
        }

        return [data];
    }

    // Initially plot the smiley face when the window loads
    window.onload = function() {
        let smileyData = generateSmileyFaceData();
        Plotly.newPlot('plot', smileyData);
    };

    function startClustering() {
        let centroids = [{x: 4, y: 7}, {x: 6, y: 7}, {x: 5, y: 4}];
        let data = generateSmileyFaceData()[0]; // Regenerate the data for clustering

        if (clusteringStep === 0) {
            // Just change the color for the first click
            changeColors(data, centroids);
            clusteringStep = 1; // Move to next step
        } else if (clusteringStep === 1) {
            // Perform clustering on the second click
            performClustering(data, centroids);
            clusteringStep = 0; // Reset or move to next step for further actions
        }

        // Update the plot
        Plotly.react('plot', [data]);
    }

    function changeColors(data, centroids) {
        // Similar to your existing color assignment logic
        data.marker.color = data.x.map((x, i) => {
            let y = data.y[i];
            let distances = centroids.map(centroid => Math.sqrt((x - centroid.x) ** 2 + (y - centroid.y) ** 2));
            let closestCentroidIndex = distances.indexOf(Math.min(...distances));
            return closestCentroidIndex === 0 ? 'red' : closestCentroidIndex === 1 ? 'green' : 'blue';
        });
    }

    function performClustering(data, centroids) {
        // Move points to their nearest centroid (this is a simplification)
        for (let i = 0; i < data.x.length; i++) {
            let x = data.x[i];
            let y = data.y[i];
            let distances = centroids.map(centroid => Math.sqrt((x - centroid.x) ** 2 + (y - centroid.y) ** 2));
            let closestCentroid = distances.indexOf(Math.min(...distances));
            data.x[i] = centroids[closestCentroid].x + (Math.random() - 0.5) * 0.5; // Adding randomness to avoid overlap
            data.y[i] = centroids[closestCentroid].y + (Math.random() - 0.5) * 0.5;
        }
        data.marker.color = 'black'; // Optional: reset colors or set to a new color after clustering
    }
</script>

</body>
</html>

