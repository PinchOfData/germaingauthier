---
permalink: /software
---

**Relatio** is a Python package to extract simple narrative statements from large text corpora (e.g., "Taxes ruin the economy.", "Democrats stole the election.", "People are losing their jobs."). 

For a given corpus, we map semantic relationships between K latent entities. The number of latent entities is chosen by the user (we offer quantitative metrics for a data-driven choice). Our package then allows users to plot narratives as directed multigraphs ([some examples](https://sites.google.com/view/trump-narratives/trump-tweet-archive)). The method is described in greater detail in the [original paper](https://arxiv.org/abs/2108.01720). 

Check out the [PyPi version](https://pypi.org/project/relatio/) and the [latest development version](https://github.com/relatio-nlp/relatio) for your own applications.


<head>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/vis/4.16.1/vis.css" type="text/css" />
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/vis/4.16.1/vis-network.min.js"> </script>
<center>
<h1></h1>
</center>

<!-- <link rel="stylesheet" href="../node_modules/vis/dist/vis.min.css" type="text/css" />
<script type="text/javascript" src="../node_modules/vis/dist/vis.js"> </script>-->

<style type="text/css">

        #mynetwork {
            width: 650px;
            height: 400px;
            background-color: #ffffff;
            border: 1px solid lightgray;
            position: relative;
            float: left;
        }

        

        

        
</style>

</head>

<body>
<div id = "mynetwork"></div>


<script type="text/javascript">

    // initialize global variables.
    var edges;
    var nodes;
    var network; 
    var container;
    var options, data;

    
    // This method is responsible for drawing the graph, returns the drawn network
    function drawGraph() {
        var container = document.getElementById('mynetwork');
        
        

        // parsing and collecting nodes and edges from the python
        nodes = new vis.DataSet([{"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "shutdown", "label": "shutdown", "shape": "dot", "size": 3}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "win", "label": "win", "shape": "dot", "size": 3}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "democrat", "label": "democrat", "shape": "dot", "size": 30}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "fair", "label": "fair", "shape": "dot", "size": 3}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "election", "label": "election", "shape": "dot", "size": 6}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "involve", "label": "involve", "shape": "dot", "size": 3}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "fake news", "label": "fake news", "shape": "dot", "size": 3}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "people", "label": "people", "shape": "dot", "size": 21}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "problem", "label": "problem", "shape": "dot", "size": 3}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "tax", "label": "tax", "shape": "dot", "size": 6}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "poll", "label": "poll", "shape": "dot", "size": 3}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "establishment special interest", "label": "establishment special interest", "shape": "dot", "size": 3}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "dems", "label": "dems", "shape": "dot", "size": 3}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "border", "label": "border", "shape": "dot", "size": 9}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "thing", "label": "thing", "shape": "dot", "size": 12}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "currency", "label": "currency", "shape": "dot", "size": 3}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "government", "label": "government", "shape": "dot", "size": 3}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "canada", "label": "canada", "shape": "dot", "size": 3}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "tariff", "label": "tariff", "shape": "dot", "size": 6}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "crime", "label": "crime", "shape": "dot", "size": 3}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "china", "label": "china", "shape": "dot", "size": 12}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "biden", "label": "biden", "shape": "dot", "size": 6}, {"color": "rgb(166, 187, 190, 0.7)", "hidden": false, "id": "country", "label": "country", "shape": "dot", "size": 21}]);
        edges = new vis.DataSet([{"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "democrat", "hidden": false, "label": "want", "to": "border", "width": 18}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "democrat", "hidden": false, "label": "support", "to": "border", "width": 4}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "democrat", "hidden": false, "label": "steal", "to": "election", "width": 5}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "democrat", "hidden": false, "label": "shut", "to": "government", "width": 5}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "democrat", "hidden": false, "label": "commit", "to": "crime", "width": 5}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "democrat", "hidden": false, "label": "raise", "to": "tax", "width": 4}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "democrat", "hidden": false, "label": "want", "to": "country", "width": 3}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "democrat", "hidden": false, "label": "hurt", "to": "country", "width": 3}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "democrat", "hidden": false, "label": "want", "to": "shutdown", "width": 3}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "democrat", "hidden": false, "label": "want", "to": "win", "width": 3}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "fake news", "hidden": false, "label": "like", "to": "thing", "width": 4}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "people", "hidden": false, "label": "love", "to": "country", "width": 5}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "people", "hidden": false, "label": "want", "to": "country", "width": 4}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "people", "hidden": false, "label": "look", "to": "people", "width": 4}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "poll", "hidden": false, "label": "look", "to": "people", "width": 5}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "establishment special interest", "hidden": false, "label": "kill", "to": "country", "width": 8}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "dems", "hidden": false, "label": "want", "to": "border", "width": 4}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "thing", "hidden": false, "label": "look", "to": "people", "width": 8}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "thing", "hidden": false, "label": "think", "to": "fair", "width": 4}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "canada", "hidden": false, "label": "look", "to": "china", "width": 3}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "tariff", "hidden": false, "label": "bring", "to": "involve", "width": 4}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "china", "hidden": false, "label": "steal", "to": "people", "width": 6}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "china", "hidden": false, "label": "manipulate", "to": "currency", "width": 4}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "china", "hidden": false, "label": "solve", "to": "problem", "width": 3}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "biden", "hidden": false, "label": "raise", "to": "tax", "width": 6}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "biden", "hidden": false, "label": "spy", "to": "election", "width": 4}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "country", "hidden": false, "label": "charge", "to": "tariff", "width": 4}, {"arrows": "to", "color": "rgba(131, 133, 143, 0.7)", "from": "country", "hidden": false, "label": "need", "to": "thing", "width": 4}]);

        // adding nodes and edges to the graph
        data = {nodes: nodes, edges: edges};

        var options = {"nodes": {"font": {"size": 20}}, "edges": {"color": {"inherit": true}, "font": {"size": 20}, "smooth": {"forceDirection": "none"}}, "physics": {"barnesHut": {"centralGravity": 0.5, "springLength": 100, "springConstant": 0.05, "avoidOverlap": 0.1}, "minVelocity": 0.75}};
        
        

        

        network = new vis.Network(container, data, options);
	 
        


        

        return network;

    }

    drawGraph();

</script>
</body>
