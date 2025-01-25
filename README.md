
Please cite this paper if you use our code or data:
```
@inproceedings{verma-etal-2023-large,
    title = "Large Scale Multi-Lingual Multi-Modal Summarization Dataset",
    author = "Verma, Yash  and
      Jangra, Anubhav  and
      Verma, Raghvendra  and
      Saha, Sriparna",
    booktitle = "Proceedings of the 17th Conference of the European Chapter of the Association for Computational Linguistics",
    month = may,
    year = "2023",
    address = "Dubrovnik, Croatia",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2023.eacl-main.263",
    pages = "3620--3632",
    abstract = "Significant developments in techniques such as encoder-decoder models have enabled us to represent information comprising multiple modalities. This information can further enhance many downstream tasks in the field of information retrieval and natural language processing; however, improvements in multi-modal techniques and their performance evaluation require large-scale multi-modal data which offers sufficient diversity. Multi-lingual modeling for a variety of tasks like multi-modal summarization, text generation, and translation leverages information derived from high-quality multi-lingual annotated data. In this work, we present the current largest multi-lingual multi-modal summarization dataset (M3LS), and it consists of over a million instances of document-image pairs along with a professionally annotated multi-modal summary for each pair. It is derived from news articles published by British Broadcasting Corporation(BBC) over a decade and spans 20 languages, targeting diversity across five language roots, it is also the largest summarization dataset for 13 languages and consists of cross-lingual summarization data for 2 languages. We formally define the multi-lingual multi-modal summarization task utilizing our dataset and report baseline scores from various state-of-the-art summarization techniques in a multi-lingual setting. We also compare it with many similar datasets to analyze the uniqueness and difficulty of M3LS. The dataset and code used in this work are made available at {``}https://github.com/anubhav-jangra/M3LS{''}.",
}
```

Complete version of the dataset can be found at the following URL:  [https://drive.google.com/drive/folders/1s57wmJJ310kzcpCVzUMleojyuO3ibPDF?usp=sharing](https://drive.google.com/drive/folders/109esyywmS7iud8Fz7AK-Us21bWoVd2rx)

To load a file from our generated dataset, we need `Python 2.7+` installed in our system

The file structure is as follows:

language_directory `language`
  - `LanguageCode_imagefolder.zip` - zipped jpg files
  - `LanguageCode_articles.zip` - zipped json files
 
 `language` is the folder containing processed articles and their corresponding images as subdirectories for any particular language within our dataset.
 
 `LanguageCode_imagefolder.zip` is the zipped folder which consists of all corresponding images in a hashed format for any article having images.
 
 `LanguageCode_articles.zip` is the zipped folder which consists of `.json` format files which contains the article text including summaries for the article and other meta information. 
 
 
 
 > NOTE: We provide the data in a compressed `.zip` format to enable ease of storage and transfer. ALL data of interest must be unzipped for the supplementary parser to function. 
 > In OS like "Linux", commands like `unzip filename.zip` can we used to decompressed the files. And "Windows" provides GUI support to decompress `.zip` format files.
 
 
#### Import necessary packages
Within `python` terminal, we need to 
```python
# import the json module and our dedicated Parser

import json
from fileparser import Parse


# enter the path to our json article
path = "path/to/a/json/file"

# define the file_loader function
def file_loader(path_to_file):
    # Loads a json file
    with open(path_to_file, encoding = 'utf-8') as f:
        data = json.load(f)
    return data
    
# execute the file_loader function
file = file_loader(path)

# create an object of our file using the Parse class
article = Parse(file)

# `article` in now an object of Parse class, and it has 10+ defined methods, which can be found in our `fileparser.py` file, the most important ones for reference now are the following three methods:

```

`get_textall()` returns a string with complete text of the article.

`get_summary()` returns the text summary of the article.

`get_keywords()` returns a list of keywords associated with the article.

`get_images(path/to/imagefolder/)` Requires path to image folder for the corresponding language, returns a list of tuples containing name of images and their captions pairs. Image name is of the format "hash of the article" ## "part of the subsection the image belongs to" ## "randomized token". Image name can be extracted from the list  and they can be found in our file directory

> NOTE that all path should be either absolute or relative to the location of `fileparser.py`.



> `M3LS` data use should be strictly in accordance with the terms and conditions mentioned by `BBC News`, hence for using this data, you agree to the terms and conditions discussed here : https://www.bbc.com/lnp/terms-and-conditions


