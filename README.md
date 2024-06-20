# Introduction
In this (personal) project, I leverage the capabilities of Google's BERT Large Language Model (as shown below), to generate hidden states for text data 

# Data Collection
The data used for this project came exclusively from Wikipedia articles. Using BeautifulSoup on Python, I collected over 400 Wikipedia articles, all falling under the topics 'Science', 'Music', 'Sports', or 'Government & Law'.
The motivation for these 4 categories were to have some very general topics (so each one would have plenty of training data), but they still need to be different "enough" to classify.
While collecting the articles, the paragraphs were split up so that each paragraph represented one sample.

Some standard text preprocessing was applied, including getting rid of stop words and punctuation.

# Hidden States Visualization
After collecting the paragraphs from Wikipedia, I simply passed them through a tokenizer and through Google's pretrained BERT model and collected their hidden states.
The 


# Hidden State Classification


# Results


# Limitations
The text data comes exclusively from Wikipedia articles, which may limit the generalization capabilities for this approach.
Also this model assumes that the input WILL fall into one of the four classes. A solution to this could be to introduce an 'other' class, which contains training data from any Wikipedia article that is not in one of the four classes.
