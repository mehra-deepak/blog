---
title: Unwinding Cosine Similarity
---

Greetings Folks,

I hope you are really doing fine.

In this article we will be going through one of the most useful Procedure used in the field of Natural Language Processing of Machine Learning and that is Cosine Similarity.
Cosine Similarity came into account as method or Algorithm to solve the Document Distance Problem.
In document distance problem we have two document D1 and D2 and all we have to do is compute the distance between them represented by:
```
      Distance=d(D1, D2)
```
Where distance means the resemblance of the two document i.e. finding out the degree of similarity between them.
In terms of Machine language a Document can be defined as the Sequence of words and a word can be defined as the sequence of alphanumeric characters. So a more precise definition or the goal for Document Distance can be presented as the idea of finding shared words between the two documents.
Let us take the Scenario where in we have two documents as .
```
            D1 =  “the dog”
            D2= “the cat”
 ```
In 3 dimensional vector space it can be visualized as :


![](https://i.imgur.com/SFjpyGw.png)


Where D1 and D2 are the respective vectors of the Document one and two.
Now in order to find the distance between these two vector we can use inner product of vector calculus also termed as dot product of two vectors, and it can be applied as:
```
d’(D1, D2) = D1.D2 = Σ (D1[W].D2[W])
```
However there is a problem with this formulation and that is it is not scale invariant, which means although it may seem to work fine for Documents with lesser words it fails to work for lengthier docs as an instance long documents with 99% of same words seem farther than short documents with 10% same words.
This was fixed by Normalization  i.e  dividing the method by the number of words in each document:
```
d’’(D1, D2) = (D1.D2)/(|D1|.|D2|)
```
where mod of document D ,|D| represents the number of words in a document. 
The geometric (rescaling) interpretation of this would be that: 
```
d(D1, D2) = arccos(d’’(D1, D2))
```
So to conclude Document Distance is the angle between the two vectors and s. An angle of 0◦ means the two documents are identical whereas an angle of 90◦ means there are no common words.
Now the question is how this Paper work and all the Analytical Stuff can be transformed into Machine Compatible Computation.In terms of Programming the notion behind mathematical computation is to represent a document D as a vector of occurrences of words W and Voila you are good to go.
Since this Algorithm came into play it has evolved quiet a lot, in terms of compensating with the Space and Time Complexity.
The fastest in terms of Compilation time has been provided below:

```
import math
import string
import sys

##################################
# Operation 1: read a text file ##
##################################
def read_file(filename):
    """ 
    Read the text file with the given filename;
    return a list of the lines of text in the file.
    """
    try:
        f = open(filename, 'r')
        return f.read()
    except IOError:
        print "Error opening or reading input file: ",filename
        sys.exit()

#################################################
# Operation 2: split the text lines into words ##
#################################################

# global variables needed for fast parsing
# translation table maps upper case to lower case and punctuation to spaces
translation_table = string.maketrans(string.punctuation+string.uppercase,
                                     " "*len(string.punctuation)+string.lowercase)

def get_words_from_line_list(text):
    """
    Parse the given text into words.
    Return list of all words found.
    """
    text = text.translate(translation_table)
    word_list = text.split()
    return word_list

##############################################
# Operation 3: count frequency of each word ##
##############################################
def count_frequency(word_list):
    """
    Return a dictionary mapping words to frequency.
    """
    D = {}
    for new_word in word_list:
        if new_word in D:
            D[new_word] = D[new_word]+1
        else:
            D[new_word] = 1
    return D

#############################################
## compute word frequencies for input file ##
#############################################
def word_frequencies_for_file(filename):
    """
    Return dictionary of (word,frequency) pairs for the given file.
    """

    line_list = read_file(filename)
    word_list = get_words_from_line_list(line_list)
    freq_mapping = count_frequency(word_list)

    print "File",filename,":",
    print len(line_list),"lines,",
    print len(word_list),"words,",
    print len(freq_mapping),"distinct words"

    return freq_mapping

def inner_product(D1,D2):
    """
    Inner product between two vectors, where vectors
    are represented as dictionaries of (word,freq) pairs.

    Example: inner_product({"and":3,"of":2,"the":5},
                           {"and":4,"in":1,"of":1,"this":2}) = 14.0 
    """
    sum = 0.0
    for key in D1:
        if key in D2:
            sum += D1[key] * D2[key]
    return sum

def vector_angle(D1,D2):
    """
    The input is a list of (word,freq) pairs, sorted alphabetically.

    Return the angle between these two vectors.
    """
    numerator = inner_product(D1,D2)
    denominator = math.sqrt(inner_product(D1,D1)*inner_product(D2,D2))
    return math.acos(numerator/denominator)

def main():
    if len(sys.argv) != 3:
        print "Usage: docdist8.py filename_1 filename_2"
    else:
        filename_1 = sys.argv[1]
        filename_2 = sys.argv[2]
        sorted_word_list_1 = word_frequencies_for_file(filename_1)
        sorted_word_list_2 = word_frequencies_for_file(filename_2)
        distance = vector_angle(sorted_word_list_1,sorted_word_list_2)
        print "The distance between the documents is: %0.6f (radians)"%distance

if __name__ == "__main__":
    import profile
    profile.run("main()")

```
However thanks to Scikit Learn and the open source contributor who have put all this hard coded stuffs into ease for lazy people like me and you by providing simple library into account.
```
sklearn.metrics.pairwise.cosine_similarity(X, Y=None, dense_output=True)
```

That’s all for today allow me to bid a very joyous goodbye.
Thanks for following up with this article wishing you luck and Happy Learning.

    

