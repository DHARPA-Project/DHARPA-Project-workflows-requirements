
# Bipartite graph with projection
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
    Performing network analysis tasks on a bipartite graph and creating a projection from it

    **Workflow curated or created by:** DH researcher
    
    **DH related example?** yes
    
=== "Examples of research questions"
    Did exposure to other soldiers serving in the same unit at the same time have an impact on their later lives (marital status, occupational change, and spatial mobility)? Did social connections made during the war have a statistically relevant impact in any of those choices? 

=== "Workflow text summary"
    One of articles I cite all the time discusses the importance of the social connections made between soldiers during the war on their later lives (i.e. all things being equal, if someone from your Great War army unit was employed in 1930, you yourself would be more likely to be employed). However, a recent article criticizing cliometrics in WWI studies noted that such studies just assume that an individual was in his first (or last) unit for the entirety of his in service, which was rarely true. Arguably, if we want a measure of how much influence Person A’s wartime connections had, the measurement of that influence should account for how strong those connections might have been, perhaps as proxied by how long Person A was actually in contact with those other people (from arpa channel discussion 18th May 2021).

=== "Workflow input"
    Nodes (2 tables) and edges (1 table)

=== "Workflow output"
    Computationally augmented nodes table</br>
    User augmented nodes table</br>
    User augmented edges table</br>
    New one-mode-graph edges table computed through projection</br>

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
