<H3>ENTER YOUR NAME : JAYAKRISHNAN L B L</H3>
<H3>ENTER YOUR REGISTER NO : 212222230052</H3>
<H3>EX. NO.6</H3>
<H3>DATE:</H3>
<H1 ALIGN =CENTER>Implementation of Semantic ANalysis</H1>
<H3>Aim: to perform Parts of speech identification and Synonym using Natural Language Processing (NLP) techniques. </H3> 
 <BR>
<h3>Algorithm:</h3>
Step 1: Import the nltk library.<br>
Step 2: Download the 'punkt', 'wordnet', and 'averaged_perceptron_tagger' resources.<br>
Step 3:Accept user input for the text.<br>
Step 4:Tokenize the input text into words using the word_tokenize function.<br>
Step 5:Iterate through each word in the tokenized text.<br>
•	Perform part-of-speech tagging on the tokenized words using nltk.pos_tag.<br>
•	Print each word along with its corresponding part-of-speech tag.<br>
•	For each verb , iterate through its synsets (sets of synonyms) using wordnet.synsets(word).<br>
•	Extract synonyms and antonyms using lemma.name() and lemma.antonyms()[0].name() respectively.<br>
•	Print the unique sets of synonyms and antonyms.
<H3>Program:</H3>

```
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize,sent_tokenize
from nltk.stem import PorterStemmer
nltk.download( 'punkt' )
nltk.download( 'stopwords' )

def preprocess_text(text):
	# Tokenize the text into words
	words = word_tokenize(text)
	# Remove stopwords and punctuation
	stop_words= set(stopwords.words( 'english'))
	filtered_words= [word for word in words if word. lower() not in stop_words and word.isalnum()]

	# Stemming
	stemmer = PorterStemmer()

	stemmed_words= [stemmer. stem(word) for word in filtered_words]
	return stemmed_words

def generate_summary(text,num_sentences=3):

	sentences= sent_tokenize(text)
	preprocessed_text = preprocess_text(text)
	# Calculate the frequency of each word
	word_frequencies =nltk. FreqDist (preprocessed_text)

	# Calculate the score for each sentence based on word frequency
	sentence_scores ={}
	for sentence in sentences:
		for word, freq in word_frequencies.items():
			if word in sentence.lower():
				if sentence not in sentence_scores:
					sentence_scores[sentence] = freq
				else:
					sentence_scores[sentence]+= freq
	# Select top N sentences with highest scores
	summary_sentences= sorted(sentence_scores, key=sentence_scores.get,reverse=True) [ : num_sentences]

	return ' '. join(summary_sentences)

if __name__=="__main__":
	input_text ="""
	Natural language processing (NLP) is a subfield of artificial intelligence.
	It involves the development of algorithms and models that enact NLP.
	NLP is used in various applications, including chatbots, language Understanding, and language generation.
	This program demonstrates a simple text summarization using NLP"""
summary = generate_summary(input_text)
print("Origina1 Text: ")
print (input_text )
print( " \nSummary : " )
print(summary)

```


<H3>Output</H3>

![image](https://github.com/user-attachments/assets/e1783c83-4c42-44fb-bc38-be1349677f64)


<H3>Result:</H3>
Thus , the program to perform the Parts of Speech identification and Synonymis was executed successfully.
