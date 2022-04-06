
# Topic modeling LDA
## 1. Data
=== "Description"
    Description of the data used
    folder containing list of text files, file names contain metadata
=== "Number of files"
    Number of files can vary, in the current example approximately 7000 text files
    

=== "Files type"
    txt
    

=== "Files alias"
    n/a as large number of files
    
    

=== "Columns"
    
    ### Table name/Data alias: 
    
    #### All
    *List of all columns*

    ||
    |---|
    |files_list|
    |files_names|

    #### Mandatory
    To be determined with pre-processing strategy. In this case, I will assume that the initial tabular data contains a files_list and file_names columns.

    #### Standardised
    standardised names to be determined



## 2. Workflow

=== "Workflow scope"
    Performing text analysis tasks on a corpus of documents

    **Workflow curated or created by/from:** 
    *DH Researcher*
    
    **DH related example?**
    *yes*

=== "Examples of research questions"
    *Please list a few examples of research questions that this workflow could help with*

=== "Workflow text summary"
    *Description of the workflow steps in a text form*

=== "Workflow input"
    Folder containing text files

=== "Workflow output"
    *Description of the expected data output for the workflow*

## 3. Steps considered

### Step 1

=== "Step name"
    Transform data sources into tabular data/exploitable format
    

=== "Description"
    

=== "Inputs"

    |Name|Type|
    |---|---|
    |files collection|corpus|


=== "Outputs"

    |Name|Type|
    |---|---|
    |corpus_table|table(files_name,files_content?(see note))|

=== "Notes"
    For the next step, files content may not be necessary yet. It may only be necessary to add the file content after filtering the corpus by date.

=== "Links to useful ressources"

### Step 2

=== "Step name"
    Get metadata
    

=== "Description"
    Get metadata contained in the files name

=== "Inputs"

    |Name|Type|
    |---|---|
    |files_name|string|
    |publications|dict or list of strings collected as user input|


=== "Outputs"

    |Name|Type|
    |---|---|
    |files_name|string|
    |date|string|
    |publication_name|string|

=== "Notes"
    Depending on the metadata to extract, users may need to input the publication names that match the reference provided in file name.
    Previews may be needed at every step.
    This step may not be applicable to all types of corpus, e.g. with social media data.

=== "Links to useful ressources"

### Step 3

=== "Step name"
    Filtering corpus by date
    
=== "Description"
    Filter corpus by date and visualise distribution

=== "Inputs"

    |Name|Type|
    |---|---|
    |files_name|string|
    |date|string|
    |publication_name|string|
    |start_date|string or date|
    |end_date|string or date|

=== "Outputs"

    |Name|Type|
    |---|---|
    |files_name|string|
    |date|string|
    |publication_name|string|

=== "Notes"
    Visualization would assist users filtering their data, they would see the modification on viz before validating the inputs.
    

=== "Links to useful ressources"
    Visualization: https://observablehq.com/@dharpa-project/timestamped-corpus

### Step 4

=== "Step name"
    Add text content in dataset
    
=== "Description"
    Retrieve .txt files content and add to dataset, if not done at step 1

=== "Inputs"

    |Name|Type|
    |---|---|
    |files_name|string|
    |date|string|
    |publication_name|string|

=== "Outputs"

    |Name|Type|
    |---|---|
    |files_name|string|
    |date|string|
    |publication_name|string|
    |document|string|

=== "Notes"
    Not sure if the text would be best added here or at the first step.


=== "Links to useful ressources"

        
### Step 5

=== "Step name"
    Removing stop words, punctuation, short words
    
=== "Description"
    Perform operations on the text to focus on the tokens that bring an interpretative value

=== "Inputs"

    |Name|Type|
    |---|---|
    |files_name|string|
    |date|string|
    |publication_name|string|
    |stop_words_list|array or csv|
    |text_processing_options|array or object|
    |document|string|

=== "Outputs"

    |Name|Type|
    |---|---|
    |files_name|string|
    |date|string|
    |publication_name|string|
    |document|string|

### Step 6

=== "Step name"
    Lemmatize
    
=== "Description"
    Lemmatize corpus

=== "Inputs"

    |Name|Type|
    |---|---|
    |files_name|string|
    |date|string|
    |publication_name|string|
    |language|string|
    |document|string|

=== "Outputs"

    |Name|Type|
    |---|---|
    |files_name|string|
    |date|string|
    |publication_name|string|
    |document|string|

=== "Notes"

=== "Links to useful ressources"

### Step 7

=== "Step name"
    LDA
    
=== "Description"
    Run LDA

=== "Inputs"

    |Name|Type|
    |---|---|
    |files_name|string|
    |date|string|
    |publication_name|string|
    |document|string|
    |filter_extremes|array or boolean|
    |hyper_parameters|array or object|
    |number_of_topics|integer or boolean|

=== "Outputs"

    |Name|Type|
    |---|---|
    |models|array or object|
    |scores|array or object|

=== "Notes"
    This step needs to be refined while iterating with code/ui

=== "Links to useful ressources"

### Step 8

=== "Step name"
    Number of topics
    
=== "Description"
    Decide on number of topics

=== "Inputs"

    |Name|Type|
    |---|---|
    |models|array of arrays or object|
    |scores|array or object|

=== "Outputs"

    |Name|Type|
    |---|---|
    |model|array|
    |score|float|

=== "Notes"

=== "Links to useful ressources"

### Step 9

=== "Step name"
    Number of topics
    
=== "Description"
    Decide on number of topics

=== "Inputs"

    |Name|Type|
    |---|---|
    |models|array of arrays or object|
    |scores|array or object|

=== "Outputs"

    |Name|Type|
    |---|---|
    |model|array|
    |score|float|

=== "Notes"


=== "Links to useful ressources"

### Step 10

=== "Step name"
    Number of topics
    
=== "Description"
    Decide on number of topics

=== "Inputs"

    |Name|Type|
    |---|---|
    |models|array of arrays or object|
    |scores|array or object|

=== "Outputs"

    |Name|Type|
    |---|---|
    |model|array|
    |score|float|

=== "Notes"


=== "Links to useful ressources"

### Step 11

=== "Step name"
    Topic visualisation
    
=== "Description"
    Visualize topics with pyLDAvis python package

=== "Inputs"

    |Name|Type|
    |---|---|


=== "Outputs"

    |Name|Type|
    |---|---|


=== "Notes"
    Inputs and outputs to be determined

=== "Links to useful ressources"

### Step 12

=== "Step name"
    Topics naming and categorisation
    
=== "Description"
    

=== "Inputs"

    |Name|Type|
    |---|---|


=== "Outputs"

    |Name|Type|
    |---|---|


=== "Notes"
    Inputs and outputs to be determined

=== "Links to useful ressources"

### Step 13

=== "Step name"
    Distribution computations
    
=== "Description"
    Compute ditributions (per topic and per document, per topic for the whole corpus, per publication)

=== "Inputs"

    |Name|Type|
    |---|---|
    |model|object or string (to be verified)|
    |corpus|document list with content|


=== "Outputs"

    |Name|Type|
    |---|---|
    |distribution_per_topic_per_doc|table|
    |distribution_per_topic_whole_corpus|table|
    |distribution_per_publication|table|


=== "Notes"
    

=== "Links to useful ressources"

### Step 14

=== "Step name"
    Distribution per topic for the whole corpus
    
=== "Description"
    

=== "Inputs"

    |Name|Type|
    |---|---|
    |corpus|document list with content|
    |distribution_computations|table|


=== "Outputs"

    |Name|Type|
    |---|---|
    |distribution_computations|table|


=== "Notes"
    

=== "Links to useful ressources"

        


## 4. Implementation
*In case of implementation, this section enables to indicate features concerned and link to the relevant DHARPA's Github repo*
