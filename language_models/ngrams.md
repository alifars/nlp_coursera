### language model
predicts the next word, given previous words
n-gram: a sequence of n words


problem: What is the probability of “Jack” given the previous word “that”: p(Jack|that) = ?

Toy corpus:

This is the house that Jack built. This is the malt that lay in the house that Jack built.
This is the rat, that ate the malt that lay in the house that Jack built.
This is the cat, that killed the rat, that ate the malt that lay in the house that Jack built.


solution:
we count bigrams: 
P(Jack | that) = count(that Jack) / count(that ..) = 4 / 10 = 0.4

language model use cases:
- text generation
- speech recognition

compute the probability of a sentences with a language model
we use chain rule to break the probaility of a sentence to probaibility of smaller pieces:
W = w1w2w3w4..wk
P(W) = p(w1) * p(w2|w1) * p(w3|w2w1) * p(w4|w3w2w1)*...*p(wk | wk-1wk-2wk-3..w1)

Markov's assumption: we don't need to look at all history, we can assume that a word is just dependent of n previous words
* we add fake START and END at the beginning and end
our equation becomes simpler (used bigrams):
P(W) = p(w1 | START) * p(w2 | w1) * p(w3 | w2w1) * p(w4|w3w2)

Would the probabilities of all possible sequences of words sum into 1? NO
#TODO
insert two formulas here


limitations of n-grams: ?
each word is a token

### Evaluate language models: perplexity

we have a probabilistic model (our n-gram model) and some data, we want to find the parameters of our model

extrinsic evaluation: end to end evaluation

likelihood = P(W_test)
perplexity = P(W_test) ^ -1/N
N : length of test corpus

the lower perplexity, the better

problem:
train corpus: this is the house that Jack buit
test corpus: this is the malt
what is the preplexity of a bigram model?

solution:
p(w_test) = p(this) * p(is | this) * p(the | is) * p(malt | the)
perplexity = P(w_test)^ -1/4 = 

two issues:
1- we have not seen word 'malt' in training data
fix: replace not seen word with <unk> token
2- we may see a new n-gram that we have not seen in the training data
fix: smoothing
  
smoothing:
add-one smoothing 
add-k smoothing
sometimes we want to use longer ngrams, but we don't have enough data:
fix1: Kats backoff
fix2: interpolation smoothing
fix3: absolute discounting: ngram distribution in test is similar to train set



  











