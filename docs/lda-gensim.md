
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
        
### Step 5

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
        


## 4. Implementation
*In case of implementation, this section enables to indicate features concerned and link to the relevant DHARPA's Github repo*
