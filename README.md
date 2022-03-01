Complete version of the dataset can be found at the following URL:  https://drive.google.com/drive/folders/1s57wmJJ310kzcpCVzUMleojyuO3ibPDF?usp=sharing

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


