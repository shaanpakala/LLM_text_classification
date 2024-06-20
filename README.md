# Introduction
In this (personal) project, I leverage the capabilities of Google's BERT Large Language Model (as shown below), to generate hidden states for text data 
<img width="765" alt="Screenshot 2024-06-20 at 3 46 38 PM" src="https://github.com/shaanpakala/LLM_text_classification/assets/68576257/4c618947-5b8f-487a-8fec-e06622983e86">

# Data Collection
The data used for this project came exclusively from Wikipedia articles. Using BeautifulSoup on Python, I collected over 400 Wikipedia articles, all falling under the topics 'Science', 'Music', 'Sports', or 'Government & Law'.
The motivation for these 4 categories were to have some very general topics (so each one would have plenty of training data), but they still need to be different "enough" to classify.
While collecting the articles, the paragraphs were split up so that each paragraph represented one sample.

Some standard text preprocessing was applied, including getting rid of stop words and punctuation.

# Hidden States Visualization
After collecting the paragraphs from Wikipedia, I simply passed them through a tokenizer and through Google's pretrained BERT model and collected their hidden states.
The issue with visualizing these hidden states, is that each sample's hidden states comes in a 2D matrix, which is not that intuitive to visualize. To solve this, I simply took the sum over axis 1. The before and after shapes are shown below (train set & test set).

<img width="346" alt="Screenshot 2024-06-20 at 3 48 43 PM" src="https://github.com/shaanpakala/LLM_text_classification/assets/68576257/d17bee64-a621-4ff5-a6c7-ffbfbb04e550">

As you can tell, this not only helps with compressing the data and making it more intuitive, but it also maps any text input to exactly 768 features, which is very useful for machine learning training.

After this step, we still have 768 features to visualize, so performing t-SNE to map these 768 features to just 2 features gives this scatter plot:
<img width="584" alt="Screenshot 2024-06-20 at 3 46 57 PM" src="https://github.com/shaanpakala/LLM_text_classification/assets/68576257/8a14e68e-ec7f-4794-8391-ecab44483653">

From here we can see even though only 2 features were generated from the original hidden states, the classes are still seemingly separable in this feature space, which is great news for a machine learning classifier.

# Hidden State Classification


# Results


# Limitations
The text data comes exclusively from Wikipedia articles, which may limit the generalization capabilities for this approach.
Also this model assumes that the input WILL fall into one of the four classes. A solution to this could be to introduce an 'other' class, which contains training data from any Wikipedia article that is not in one of the four classes.
