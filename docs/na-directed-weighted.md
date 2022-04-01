
# Directed weighted graph
## 1. Data
=== "Description"
    Network data from journals in the field of psychiatry and allied fields
=== "Number of files"
    2
=== "Files type"
    csv
=== "Files alias"
    *Files alias is to simplify references to datasets for present doc*
    
    * nodes

    * edges

=== "Columns"
    
    ### Table "nodes"
    
    #### All
    ||
    |---|
    |Id|
    |Label|
    |City|
    |CountryNetworkTime|
    |PresentDayCountry|
    |Latitude|
    |Longitude|
    |Country|

    #### Mandatory
    Id

    #### Standardised
    Id, Label

    ### Table "edges"
    
    #### All

    ||
    |---|
    |Source|
    |Target|
    |Weight|

    #### Mandatory
    Source, Target

    #### Standardised
    Source, Target, Weight


## 2. Workflow

=== "Workflow scope"
    Directed weighted network analysis, nodes and edges augmentation

    **Workflow curated or created by:** DH researcher
    
    **DH related example?** yes

=== "Examples of research questions"
    *Please list a few examples of research questions that this workflow could help with*

=== "Workflow text summary"
    (from https://github.com/DHARPA-Project/NetworkXAnalysis)</br>
    **1. Import data**
    <ul>
    <li>Alternative data import</li>
    Extract nodes and edges from single file</br>
    Preview nodes and edges list
    <li>Import data from edge list using pandas</li>
    Generate graph from edgelist
    <li>Add nodes and nodes attributes</li>
    </ul>
    **2. Get information about the generated graph and its properties**
    <ul>
    <li>Test if nodes and edges correctly imported</li>
    <li>Get number of nodes and edges</li>
    <li>Get info about the augmented graph: average in degree, average out degree</li>
    </ul>
    **3. Make some basic calculations to obtain more graph properties**
    <ul>
    <li>Density</li>
    <li>Find neighbors, successors and predecessors of individual nodes</li>
    <li>Find the shortest path between two nodes, display shortest path length</li>
    </ul>
    **4. Visualize the graph**
    <ul>
    <li>Export graph to graphml file</li>
    <li>Import graphml with igraph</li>
    <li>Use Fruchterman-Reingold layout and draw with igraph</li>
    </ul>
    **5. Find largest component**
    <ul>
    <li>Convert graph to undirected</li>
    <li>Print info about the graph in its undirected form: number of nodes, number of edges, average degree</li>
    <li>Find out if there is more than 1 component in graph</li>
    <li>Get list of connected components</li>
    <li>Get largest connected component and display its nodes</li>
    <li>Create subgraph (which will be returned as an indirect graph)</li>
    <li>Get info: number of nodes, number of edges, average degree</li>
    <li>Use largest component to create a directed subgraph</li>
    <li>Get directed subgraph info: number of nodes, number of edges, average in degree, average out degree</li>
    <li>Make some calculations for undirected graphs: diameter</li>
    <li>Find clusters that have strong connectivity</li>
    <li>Visualise clusters that have strong connectivity</li>
    <li>Alternate method: find and remove isolated nodes to create a subgraph, and then display number of nodes, edges, in degree, out degree, and density</li>
    </ul>
    **6. Make some centrality calculations**
    <ul>
    <li>Calculate degrees, in degree, weighted degree, weighted in-degree, weighted out degree, and add as attribute, sort nodes by the metrics just calculated / display top n nodes according to these metrics</li>
    <li>Calculate, degree centrakity, betweenness centrality, eigenvector centrality, add as attributes, sort, print top n nodes</li>
    </ul>
    **7. Community detection**
    <ul>
    <li>export nx graph to graphml file</li>
    <li>create new infograph graph from file</li>
    <li>use Fruchterman-Reingold layout</li>
    <li>show list of unconnected nodes and remove them</li>
    <li>draw the graph with igraph</li>
    <li>export data to gefx and wisualise in Gephi</li>
    </ul>
    **8. Updating graph**
    <ul>
    <li>Extract nodes and edges from additional file</li>
    <li>Display and sort new nodes</li>
    <li>Add new nodes to graph</li>
    <li>Display graph info: number of nodes, number of edges, average in degree, average out degree</li>
    <li>Create new graph from new edges and add them to old graph</li>
    <li>Display graph info: number of nodes, number of edges, average in degree, average out degree</li>
    <li>Visualise graph</li>
    <li>Get largest component from new graph and display info: number of nodes, edges, average in degree, average out degree</li>
    </ul>


    

=== "Workflow input"
    Nodes and edges tables

=== "Workflow output"
    Computationally augmented nodes table</br>
    User augmented nodes table</br>
    User augmented edges table</br>

## 3. Steps considered

### Step 1

=== "Step name"
    Create graph object and computations

=== "Description"


=== "Inputs"

    |Name|Type|
    |---|---|
    |Edges|Table|
    |Nodes|Table|
    |Col name for source|string|
    |Col name for target|string|
    |Edge attributes|boolean|

=== "Outputs"

    |Name|Type|
    |---|---|
    |Graph object||
    |Graph properties|Table(Number of nodes, number of edges, average in-degree, average out-degree, network density)|
    |Augmented nodes|Table(nodes degree, in-degree, out-degree, weighted degree, weighted in-degree, weighted out-degree added, degree centrality, betweenness centrality, eigenvector centrality)|
    |Isolated nodes|array|
    |Direct neighbours of nodes|Table(Node id, array of outgoing connections ID)|
    |Predecessors|Table(Node Id, array of incoming connections ID)|
    |All neighbours|Table(Node Id, array of neighbours ID)|
    |Weighted shortest path|Table(Node Id, array of nodes ID)|
    |Shortest path|Table(Node Id, array of nodes ID)|
    |Undirected graph computations|Graph diameter|
    |Communities|Array of arrays|

=== "Notes"
    If there’s an error about edges or nodes computation as graph object, user needs to be made aware of it.</br>
    UI should display the list of nodes and edges with attributes.</br>
    For now everything is pre-computed (neighbours, shortest path), but a more efficient strategy may be to generate them on the fly, but the possibility for bi-directionality in such use case needs to be confirmed.</br>
    To be verified/thought through: the largest component may be a distinct step, or the same one with different nodes and edges, since it's possible that it would be the same module/viz ran again with only the nodes and edges of largest component.</br>
    To be verified/thought through: the conversion to undirected may call to another module that would be for directed graph: I don't think that it will be possible to recursively convert to directed/undirected within same module

=== "Questions"
    Are the undirected computations presented in this notebook all relevant for a directed graph?</br>
    Is the removal of isolated nodes only relevant for viz display or would users need to remove them in graph object?</br>
    I read (externally, in a book) that, for example, the density measure need to be considered carefully in some cases, especially for valued graphs, is this relevant here, and where would this info be displayed in the requirements gathering (this will brought up as meeting item as this is more of a general discussion)</br>
    Part about convert graph to undirected to be clarified (is there a reason subgraphs are computed in this section?)

### Step 2

=== "Name"
    Augmentation for nodes and edges table

=== "Description"

=== "Inputs"    

    Same as step 1, with additionally:

    |Name|Type|
    |---|---|
    |Modified nodes|Table(nodeID, modified columns)|
    |Modified edges|Table(edgeID, modified columns)|

=== "Outputs"

    Same as step 1, with additionally:

    |Name|Type|
    |---|---|
    |User augmented nodes table|Table|
    |User augmented edges table|Table|

=== "Notes"
    A strategy needs to be defined, so that from an UI perspective, users can re-run step 1 with data augmentation performed at step 1.

=== "Questions"

## 4. Implementation