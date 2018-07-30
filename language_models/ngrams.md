language model: predicts the next word, given previous words
n-gram: a sequence of n words


problem: What is the probability of “Jack” given the previous word “that”: p(Jack|that) = ?

Toy corpus:

This is the house that Jack built. This is the malt that lay in the house that Jack built.
This is the rat, that ate the malt that lay in the house that Jack built.
This is the cat, that killed the rat, that ate the malt that lay in the house that Jack built.


solution:
we count bigrams: 
P(Jack | that) = count(that Jack) / count(that ..) = 4 / 10 = 0.4
