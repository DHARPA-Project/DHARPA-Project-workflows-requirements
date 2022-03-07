
# Bipartite graph
## 1. Data
=== "Description"
    Network data concerning soldiers and the units they served in
=== "Number of files"
    3
=== "Files type"
    csv
=== "Files alias"
    *Files alias is to simplify references to datasets for present doc*
    
    * nodes1
    * nodes2
    * edges

=== "Columns"
    
    ### Table "nodes1"
    
    #### All
    ||
    |---|
    |SoldierId|
    |entrynoout|
    |Branch|
    |entmeth2|
    |outmeth3|
    |ENTlat|
    |ENTlong|
    |YOB|
    |isknowfarming|

    #### Mandatory
    Id (here SoldierId)

    #### Standardised
    Id

    ### Table "nodes2"
    
    #### All
    ||
    |---|
    |UnitId|
    |unitname|

    #### Mandatory
    Id (here UnitId)

    #### Standardised
    Id

    ### Table "edges"
    
    #### All

    ||
    |---|
    |Source|
    |Target|
    |unitduration|

    #### Mandatory
    Source, Target

    #### Standardised
    Source, Target, Weight (here unitduration)


## 2. Workflow

=== "Workflow scope"
    Undirected bipartite network analysis
    Undirected multigraph network analysis

    **Workflow curated or created by:** DH researcher
    
    **DH related example?** yes

=== "Workflow input"
    Nodes (2 tables) and edges (1 table)

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
    |Nodes|Table|
    |Col name for source nodes1|string|
    |Col name for target nodes1|string|
    |Col name for source nodes2|string|
    |Col name for target nodes2|string|
    |Edge attributes|boolean|

=== "Outputs"

    |Name|Type|
    |---|---|
    |Graph object||
    |Graph properties|Table(Number of nodes, number of edges, average degree)|
    |Computationally augmented nodes|Table(nodes degree, degree centrality, betweenness centrality, eigenvector centrality)|
    |Isolated nodes|array|
    |Neighbours|Table(Node Id, array of neighbours ID)|
    |Shortest path|Table(Node Id, array of nodes ID)|
    |Edges duplicates|Table(Source Id, Target ID, unitduration)|
    |Connected|Array[Boolean (isconnected?), if connected: number of connections]|
    |Largest component|graph object|

=== "Notes"
   

=== "Questions"

### Step 2

=== "Name"
    Augmentation for nodes and edges table

=== "Description"

=== "Inputs"    

    Same as step 1, with additionally:

    |Name|Type|
    |---|---|
    |Modified nodes1|Table(nodeID, modified columns)|
    |Modified nodes2|Table(nodeID, modified columns)|
    |Modified edges|Table(edgeID, modified columns)|

=== "Outputs"

    Same as step 1, with additionally:

    |Name|Type|
    |---|---|
    |User augmented nodes1 table|Table|
    |User augmented nodes2 table|Table|
    |User augmented edges table|Table|

=== "Notes"

    A strategy needs to be defined, so that from an UI perspective, users can re-run step 1 with data augmentation performed at step 1.

=== "Questions"

### Step 3

=== "Step name"
    Create multigraph object and computations

=== "Description"


=== "Inputs"

    |Name|Type|
    |---|---|
    |Edges|Table|
  

=== "Outputs"

    |Name|Type|
    |---|---|
   

=== "Notes"
   

=== "Questions"
This step needs further clarification, I didn't understand if the graph is now bi-directed + multi

## 4. Implementation