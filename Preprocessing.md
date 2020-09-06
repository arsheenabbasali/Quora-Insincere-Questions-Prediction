## [Overview](README.md)

# Preprocessing

## [Model Building](Model%20Building.md)

## [Conclusion](Conclusion.md)

As we are dealing with Natural Language Data, the cleaning process is bit different than usual numeric data. Here we first divied whole sentences in to small pieces of words using Tokenization method.  
1. **Tokenization**: Tokenization is to convert sentences to words. It is the process of dividing text into a set of meaningful pieces. These pieces are called *tokens*. We can divide a chunk of text into words, or we can divide it into sentences. Depending on the task at hand, we can define our own conditions to divide the input text into meaningful tokens. Let's take a look at how to do this.  
2. **Down-Casing**: It is a method of converting a string from uppercase to lowercase.  
3. **Filtering non-alpha characters**:  Next, we removed non-alpha characters, keeping only alphabetic characters.  
4. **Filtering stop words and punctuations**: Stop words are the commonly used words which are generally ignored by any text processing system. It is important to remove these words from our data as we would not want these words taking up space in our database, or taking up valuable processing time.  
5. **Stemming**: Stemming is the process of reducing inflection in words to their root forms such as mapping a group of words to the same stem even if the stem itself is not a valid word in the Language. Stemming is the process of producing morphological variants of a root/base word. 

Here is the function which is used to preprocess the data. It includes *word_tokenize* function to break the sentences into words then tokens are lowercased and all non-alpha words are removed. After that, stopwords are identified using pre-defined list of english stopwords from NLTK corpus and removed from the bag of tokens. After removing of all unnecessary words, the remaining tokens are stemmed using *Porter Stemmer* to level them down to their root words.

```Python
def data_processing(df):
    stemmer= PorterStemmer()
    
    # Word Tokenization
    df['Tokens'] = df['question_text'].apply(lambda TrainingData: word_tokenize(TrainingData))
    
    # Lowercase each word
    df['Tokens'] = df['Tokens'].apply(lambda x: [item.lower() for item in x])
    
    # Keeping only alpha characters
    df['Tokens'] = df['Tokens'].apply(lambda x: [item for item in x if item.isalpha()])
    
    # Removing stop words
    df['Tokens'] = df['Tokens'].apply(lambda x: [item for item in x if item not in stop_words])
    
    # Stemming
    df['Tokens'] = df['Tokens'].apply(lambda x: [stemmer.stem(item) for item in x]) 
     
    return df    
 ```
 The above function will add a new column to the datafram as *Tokens* and will show result as follows:
 
 |question_text|	target|	Tokens|
 |---------|------------|-------------|
|How did Quebec nationalists see their province...|	0	|'how', 'quebec', 'nationalist', 'see', 'provi...
|Do you have an adopted dog, how would you enco...	|0	|'Do', 'adopt', 'dog', 'would', 'encourag', 'p...
|Why does velocity affect time? Does velocity a...	|0	|'whi', 'veloc', 'affect', 'time', 'doe', 'vel...
|How did Otto von Guericke used the Magdeburg h...	|0	|'how', 'otto', 'von', 'guerick', 'use', 'magd...
|Can I convert montra helicon D to a mountain b...	|0	|'can', 'I', 'convert', 'montra', 'helicon', '...
|Is Gaza slowly becoming Auschwitz, Dachau or T...	|0	|'Is', 'gaza', 'slowli', 'becom', 'auschwitz',...
|Why does Quora automatically ban conservative ...	|0	|'whi', 'quora', 'automat', 'ban', 'conserv', ...
|Is it crazy if I wash or wipe my groceries off...	|0	|'Is', 'crazi', 'I', 'wash', 'wipe', 'groceri'...
|Is there such a thing as dressing moderately, ...	|0	|'Is', 'thing', 'dress', 'moder', 'differ', 'd...
|Is it just me or have you ever been in this ph...	|0	|'Is', 'ever', 'phase', 'wherein', 'becam', 'i...

The last step is to vectorize each word. 

6. **Vectorization**: Vectorization is used to speed up the Python code without using loop.  - Using such a function can help in minimizing the running time of code efficiently.
