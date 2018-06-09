---
layout: post
title: My Cipher Coding Strategy
---

## Principle

- the source code is supposed to be simple
- the result code is supposed to be complex
- the coding is supposed to be reporducable and secret

What's more, I only has to remember one set of real code and able to use unique and complex passwords thru sites.

Forgotten the result code, it has to able to be reporduced at any time and only by myself.

## Strategy

1. Use a set of simple numbers easy to remember or meaningful as the source code. And the password you used to use is just pretty fine, e.g. `760950760950...` or `123412341234...`
1. To keep the code unique, choose an alias base on the site. e.g. `github.com`
1. Convolute the code by the real code times with the index map.
1. If the code is a character and the corresponding real code is even, recode it and capitalize it if a character turns out.
1. Resort the result code by the source code.

## Security

To generate the result code, we need 4 sources:

- the source code
- the alias
- the index map
- the coding strategy

The first and last ones are easy to remember. And the first one might be guessable, but the last one isn't.

It's reliable because:

- the alias is short and mostly not realistic words
- the real indexing are flexible recoording the alias and the source code
- the numbers and symbols could be quite confusing

This reasons make the traditional frequency check futility. And the last two steps of the strategy make the brute force even with the real index map we are utilizing almost no differens to just brute force a password consists symbols and capital letters(almost impossible).

So, you can record you alias and the index map in any text or email as a cheat. If they are vulnerable or even barely exposed to someone unfortunatly, as long as you kept the source code to yourself, even when that one guessed out the cypher strategy schema, it's still almost uncrackable since some parts of the result code is just misleading.

## Illustrate

And let me explain how the steps work, taking github as example.

### Cut segments

```latex
alias:        github.com
source code: (7609507609)50
```

### First indexing

g -> 9 -> q -> 5 -> % -> b -> x -> 4

i -> l -> 1 -> ! -> g -> 9 -> q

t

h -> 6 -> @ -> t -> z -> 2 -> @ -> t -> z -> 2

u -> 1 -> ! -> g -> 9 -> q

b

.

c -> 4 -> # -> j -> i -> l -> 1 -> !

o -> c -> 4 -> # -> j -> i -> l

m

Notice that some of them will go into a loop, which could be avoided, but that just doesn't matter as it's long enough like `@ -> t -> z -> 2 -> @`.

### Reindexing

```latex
indexed:     4qt2qb.!lm
source code: _60__0__0_
reindexed:   44T2qB.!Lm
```

### Resorting

```latex
reindexed:   44T2qB.!Lm
source code: 7609507609
resort:        0
               0  1
               0  1  2
               0 31  2
              40 31  2
             ...
             6408317529
result:            4
                 4 4
             T   4 4
             T   4 4 2
             ...
             TBLq4!4.2m
```

### Result

`TBLq4!4.2m`

Cool, it looks just like generated randomly.

## Too complicated

You may find it too complicated that the result code is reproducable but it's just not so easy. The interesting thing is that what if I mistaked the producing at first time ? The account is sucked into vacuum now.

For one solution, you may create a map that not so random, it should goes to a circle. That you may record your map like: `1!g9q5%bx4#ji...1`, than that's much more easy to kept the code in small size and generate code conveniently.

In another way, you may need a script to generate the code for you programmaticly. You just have to set the index map and then input the source code and alias. But the problem is, as mentioned previously, it just takes a glimp for the bad guy to accquire the coding strategy, which means the most secure part of our cypher system is exposed.

And the problem now becomes to how to protect the script ? But fortunatly, it's much more easy to keep a script in physical world than keep a password on the Internet.

## Indexing map

Notice that though it doesn't matter how this map looks like, most of the below are indexed by shapes, except the symbols, actually the connection between them and some of the characters is based on Chinese pronunciation :)

Anyway, this is an **example**, you can always produce a map that's easy to remember or reproduce.

### Numbers

- 1 -> !
- 2 -> @
- 3 -> 3
- 4 -> #
- 5 -> %
- 6 -> @
- 7 -> j
- 8 -> &
- 9 -> q
- 0 -> o

### Characters

- a -> 1
- b -> x
- c -> 4
- d -> g
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
- o -> c
- p -> q
- q -> 5
- r -> 2
- s -> 4
- t -> z
- u -> 1
- v -> y
- w -> m
- x -> 4
- y -> i
- z -> 2

### Symbols

- ! -> g
- @ -> t
- \# -> j
- % -> b
- & -> h
