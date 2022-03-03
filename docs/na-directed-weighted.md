
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
    |Directed|boolean|

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
    |Undirected graph computations|Graph diameter</br>if there are multiple sub components:</br>Table of largest component nodes</br>Table of largest component edges</br>Info array for largest component(Number of nodes, number of edges, average in-degree, average out-degree)</br>Array of strongly connected component</br>Subgraph object of strongly connected component|
    |Communities|Array of arrays|

=== "Notes"
    If there’s an error about edges or nodes computation as graph object, user needs to be made aware of it.</br>
    UI should display the list of nodes and edges with attributes.</br>
    For now everything is pre-computed (neighbours, shortest path), but a more efficient strategy may be to generate them on the fly, but the possibility for bi-directionality in such use case needs to be confirmed.

=== "Questions"
    Are the undirected computations presented in this notebook all relevant for a directed graph?</br>
    Is the removal of isolated nodes only relevant for viz display or would users need to remove them in graph object?

## Step 2

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