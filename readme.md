# Building local RAG pipelines

Build a Local Retrieval Augemented Generation Pipeline from scratch: 

[![Everything Is AWESOME](https://i.ytimg.com/vi/qN_2fnOPY-M/sddefault.jpg)](https://www.youtube.com/watch?v=qN_2fnOPY-M&t=18797s)

Based on this video, I have developed a local RAG pipeline on a colab notebook with GPU enabled. I have broken down tutorials into 3 parts to better understand the process. 
Here are the links to the notebooks:

1. [Data Preprocessing](https://github.com/kavyajeetbora/nlp_doc/blob/master/notebooks/01_data_preprocessing.ipynb): In this step, we will prepare the text for processing, includes
    - Extract the text from PDFs
    - Clean the text
    - chunking the text manually
    - Embedding the chunks into a database, in this case we have exported to csv
    - for embedding the chunks we will use the all-MiniLM-L6-v2, which is small and efficient. It can run efficiently in CPU as well because of its small size. This can be helpful when the GPU is not available on colab notebook

2. [Developing a simple RAG pipeline](https://github.com/kavyajeetbora/nlp_doc/blob/master/notebooks/02_simple_RAG_pipeline.ipynb): Given a query/keyword, search the most relevant text and return
    - We will search the most relevant text from the chunks of the pdf using cosine similarity
    - Based on the search we will return the top-k relevant passages
    - These relevant passages will be to augment our query to the LLM model so improve the outcome of the text generation

3. [Local LLM](https://github.com/kavyajeetbora/nlp_doc/blob/master/notebooks/03_local_LLM.ipynb) : We will setup the local llm and implement the RAG pipeline to it
    - we will setup the local llm in colab environment
    - In this case we will use `google/gemma-2b-it` model
    - You require to generate a huggingface token to download the model
    - Once the local LLM is setup, we will create a pipeline to query the LLM with augmented context we created in step 2.
