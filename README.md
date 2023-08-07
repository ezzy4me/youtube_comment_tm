# YouTube Comments Topic Modeling 🚩
- [x] eidtting now.
- [ ] read me
- [ ] step1. annotation
- [ ] step2&3. annotation
      
This is example Coalab code for youtube comment crawling topic modeling.

This example aims to crwal YouTube comments, load them from CSV files, preprocess the data, and conduct Topic Modeling using BERTopic. 

We conducted on subject 'living alone' youtuber. It primarily includes the following stages:

## Preparation!
- Google colabatory account : https://colab.research.google.com/
- Google Play Developer API key : https://developers.google.com/android-publisher/getting_started

## Dependencies
> Pandas : 1.5.3
> 
> Numpy : 1.22.4
> 
> BERTopic : 0.15.0
> 
> SentenceTransformer : 2.2.2
> 
> pytube : 15.0.0
> 
> Google Chrome : 115

## 1. Crawling youtube data
```
step.1_ youtube_comment_crawling.ipynb
```
We first obtain video information for each youtuber and extract **video IDs** from a given YouTube video URL[^1]. We also have defined a function to get **comments and descriptions** of YouTube videos using that video ID. Collect information, including **comments on YouTube videos**, and check the title and URL of the video in question separately. 

**Please check the code for detailed annotation.**

[^1]: copy all the videos title and URLs from a youtube channel to an excel sheet using softexpert. [Ref](https://www.youtube.com/watch?v=GcjdHWVo3gA)

## 2. Data Preprocessing
The data, including YouTube comments stored in CSV format, is loaded from a specified drive path. Comments and titles are further cleaned, masked, and processed. Quantiles are computed for length-based filtering, and the dataset is sampled and concatenated. The final DataFrame is used to combine titles and comments. 

This stage involves several cleaning and processing steps:

> - **Basic Cleaning**: Removal of emojis, numbers, and other non-essential characters.
> - **Duplicate Removal**: Removal of duplicate comments reduces the dataset's size.
> - **URL Removal**: Comments containing "http" or "www" are removed.
> - **Text Length Filtering**: Comments and titles below or above specified quantiles are removed to control the data's quality.
> - **Sampling**: Comments are sampled according to log count percentage to mitigate imbalance.
> - **Special Characters Handling**: Unwanted punctuation and spaces are cleaned.
> - **YouTube Names Masking**: YouTube channel names are masked to a common identifier.
> - **Text Concatanation** : Video titles and comments are combined for further processing(i.e. [title;comment]).

## 3. BERTopic Modeling
The data is prepared for Topic Modeling through the BERTopic library. The UMAP model is configured for dimension reduction, and CountVectorizer for text vectorization. The BERTopic model is then initialized, and topic modeling is performed using specified sentence embeddings. Visualization of topics and barcharts is also provided.

BERTopic modeling is conducted using specified UMAP and CountVectorizer models, followed by visualization of the results.

more inforamtion : [BERTopic Official Page](https://maartengr.github.io/BERTopic/index.html)

## Code Snippets for Main Functions
The code provides several functions for text preprocessing, such as remove_special_characters, replace_single_u, remove_http_www, mask_youtube_names, and process_string. These functions employ regular expressions and string manipulations to clean and prepare the text data.


