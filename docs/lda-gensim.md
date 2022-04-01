
# Name of the example
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
    |date|string|
    |publication_name|string|

=== "Notes"
    Depending on the metadata to extract, users may need to input the publication names that match the reference provided in file name.

=== "Links to useful ressources"
    



## 4. Implementation
*In case of implementation, this section enables to indicate features concerned and link to the relevant DHARPA's Github repo*
