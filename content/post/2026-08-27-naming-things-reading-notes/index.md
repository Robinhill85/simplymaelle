---
title: "Reading notes on Naming Things by Tom Benner"
date: '2026-08-27'
slug: naming-things-reading-notes
output: hugodown::hugo_document
tags:
  - good practice
  - books
---

[Naming Things by Tom Benner](https://www.namingthings.co/) a tiny but neat book about the naming of identifies in code (variables, classes, methods, so not packages or libraries).
It had entered my to-read list a few years ago, when I read the blog post [Naming Things by Vicki Boykis](https://vickiboykis.com/2023/06/29/naming-things/).
Tom Benner's book is self published and available from Amazon (e-book and paperback) and [Leanpub](https://leanpub.com/naming-things) (e-book). 
I rarely buy stuff on Amazon, and prefer to read on paper, so I patiently waited for a copy to appear on my favorite second-hand book website.

## Why read about naming things yet again?

At this point, I've been exposed to much advice on naming things, in [The Art of Readable Code](https://www.oreilly.com/library/view/the-art-of/9781449318482/), [A Philosophy of Software Design](/2023/10/19/reading-notes-philosophy-software-design/), [The Programmer's Brain](/2026/08/21/the-programmer-s-brain-reading-notes/)...
So why bother read yet another source of information on the topic?
Well, I trusted Vicki Boykis' recommendation, and since the book is so short -- less than 100 pages, it wasn't a dangerous bet.

The book is well organized, easy to read, and feels exhaustive.
It explains why naming is important, why it is difficult, and presents 4 principles for naming: understandability, conciseness, consistency, distinguishability.

Here are some of my highlights...

## Bad names, bad look

Among the numerous reasons why bad names are harmful for a project, this one caught my attention:

> "[A] newcomer may develop a poor perception of the project and in the worst case, a poor perception of the team."

## What is an understandable name?

> "An understandable name has high comprehension (it can be understood quickly) and high recall (it can be remembered easily)."

It reminds me of The Programmer's Brain.

The book also recommends to avoid cleverness or irrelevant concepts: calling things based on some obscure joke or musical reference.

## The ladder of abstraction

The book advises to use the "appropriate level of abstraction".

> "Do not use a name that's so specific that you're providing information that's irrelevant to the audience, and do not use a name that's so generic that it provides little or no relevant information to them."

The book then discusses 4 names for a function that removes leading and trailing whitespace[^trimws] from a phone number: `process()`, `format()`, `trim_whitespace()`, `strip()`.
The right choice is explained to be `format()`: it shows the intent of the function without disclosing details that might be irrelevant or subject to change.

[^trimws]: Do you know about the base R `trimws()` function? Very handy.

## Booleans

The book recommends to always add `is_` in the name of Booleans, e.g. `is_valid`.

It also states that they should be stated in the positive, with an example that I'm adapting to R below:

```r
# Bad
if (!user_is_invalid) {
  save(user)
}

# Good

if (user_is_valid) {
  save(user)
}

```

This example resonated with me because it happens often to me to create a Boolean, use it with an `if` only to realize I should define the contrary of that Boolean instead.

And it reminds me, beyond naming, of negation-related rules in linters such as Jarl: [`comparison_negation`](https://jarl.etiennebacher.com/rules/comparison_negation), [`outer_negation`](https://jarl.etiennebacher.com/rules/outer_negation).

## The cost of renames

The book discusses the costs of a bad name (that add up over time: slow comprehension, low recall) and of a rename (one-time cost).
It made me think of the renaming we did and do in igraph, including the batch renaming of functions with dots in them to snake-case equivalent (along with the correct [lifecycle harness](https://lifecycle.r-lib.org/articles/communicate.html) :innocent:): work for us but also for maintainers of reverse dependencies and direct users of the package.

## Conclusion

Naming Things is a useful short read.
After reading it, I feel I pay even more attention to names in the code I was writing of reviewing. :smile_cat:
