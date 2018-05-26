---
layout: post
title: My Cryptic Codes Generating Strategy
---

## principle

- the source code should be simple enough and would like to be the only one
- the result code should be unique and complex
- the result code is supposed to be reproducable at any time

Which means, I only has to remember the only real code and able to use unique and complex passwords thru sites.

Sure, there is aother thing need to be kept in mind. I mean the index map. Here is an
example for a map that's easy to remember, you can just produce a map on your own.

## strategy

1. The real code just need to be some numbers, e.g. 7609576095...
1. To keep the code unique, create it base on the site. e.g. github
1. To hide the encoding strategy, convelute the code by the real code times.
1. If the code is a character and the real code is even, capitalize it.

And let me explain how the step.3 works.

github -> (760957)6095

g -> 9 -> % -> b -> 6 -> @ -> t -> 7

i -> l -> 1 -> ! -> g -> 9 -> %

t

h -> 6 -> @ -> t -> 7 -> j -> i -> l -> 1 -> @

u -> 1 -> @ -> t -> 7 -> j

b -> 6 -> @ -> t -> 7 -> j -> i -> l

So the result code is `7%t@jl`. Then the step.4 capitalize it into `7%T@jL`.
Cool, it looks just like generated randomly.

Notice that some of them will go into a loop, which could be avoided, but that just doesn't matter as it's long enough like `@ -> t -> 7 -> j -> i -> l -> 1 -> @`.

The flaw is that were you mistaken the code at first time, unfortunately, it's a catastrophe. So I may provide an example script that generates codes in this way.

## coding map

Notice that most of the below are indexed by shapes, except the symbols, actually the connection between them and some of the characters is based on Chinese pronunciation :)

Anyway, this is an **example**, you can always produce a map that's easy to remember or reproduce.

### numbers

- 1 -> !
- 2 -> @
- 3 -> 3
- 4 -> #
- 5 -> %
- 6 -> @
- 7 -> j
- 8 -> &
- 9 -> %
- 0 -> o

### characters

- a -> @
- b -> 6
- c -> 4
- d -> d
- e -> 4
- f -> 4
- g -> 9
- h -> 6
- i -> l
- j -> i
- k -> 7
- l -> 1
- m -> 8
- n -> 9
- o -> 0
- p -> q
- q -> 9
- r -> 2
- s -> 4
- t -> 7
- u -> 1
- v -> y
- w -> m
- x -> 4
- y -> i
- z -> 2

### symbols

- ! -> g
- @ -> t
- \# -> j
- % -> b
- & -> h
