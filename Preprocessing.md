# Preprocessing

As we are dealing with Natural Language Data, the cleaning process is bit different than usual numbers data. Here we first divied whole sentences in to small pieces of words using Tokenization method.   
1. **Tokenization**: Tokenization is to convert sentences to words. It is the process of dividing text into a set of meaningful pieces. These pieces are called *tokens*. We can divide a chunk of text into words, or we can divide it into sentences. Depending on the task at hand, we can define our own conditions to divide the input text into meaningful tokens. Let's take a look at how to do this.

After Tokenization, we need to make all the words in lower-case alphabets as strings can be case-sensitive and to avoid the problem of word duplication with upper and lower cases.  
2. **Down-Casing**: It is a method of converting a string from uppercase to lowercase. 

As we dealing here with the sentiments of the words in the questions, we do not need any numeric or special character data in our sentences.   
3. **Filtering non-alpha characters**:  Next, we removed non-alpha characters, keeping only alphabetic characters.

High frequency of Stop words like what, he/she, is, the etc. can make our model accuracy worse. That's why the next step is to remove stop words from the tokens.  
4. **Filtering stop words and punctuations**: Stop words are the commonly used words which are generally ignored by any text processing system. It is important to remove these words from our data as we would not want these words taking up space in our database, or taking up valuable processing time.

It is a very important step in Natural Language data cleaning where we Stem the tokens to its root words to avpid changes caused my the use of tense in the sentences.  
5. **Stemming**: Stemming is the process of reducing inflection in words to their root forms such as mapping a group of words to the same stem even if the stem itself is not a valid word in the Language. Stemming is the process of producing morphological variants of a root/base word. 

The last step is to vectorize each word.  
6. **Vectorization**: Vectorization is used to speed up the Python code without using loop.  - Using such a function can help in minimizing the running time of code efficiently.
