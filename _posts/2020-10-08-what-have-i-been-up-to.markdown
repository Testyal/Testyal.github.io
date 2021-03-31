---
layout: post
title:  "What have I been up to since finishing the mthree course"
date:   2020-10-26 14:00 +0000
---
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.css" integrity="sha384-zB1R0rpPzHqg7Kpt0Aljp8JPLqbXI3bhnPWROx27a9N0Ll6ZP/+DiW/UqRcLbRjq" crossorigin="anonymous">

## Calculus of Variations

It's been a year and a half since I last did any math, so I went back to the [Calculus of Variations](https://warwick.ac.uk/fac/sci/maths/people/staff/filip_rindler/calculusofvariations), returning to the chapters on Young measures and quasiconvexity (in the sense of Morrey) in particular. I've gone through these chapters like 5 times already, so I'm not learning anything new, but goinng through them again much slower than before is a good way to expose any gaps in my knowledge and clear up any wizardry happpening in the proofs. To be honest, most of the proofs involve some wizardry, guess I can't do much about that. One of the proofs in particular uses the [Hardy-Littlewood maximal function](https://en.wikipedia.org/wiki/Hardy–Littlewood_maximal_function) to establish equiintegrability of a particular subsequence of gradients. It's probably easy to see why it should be used if you've had experience in its ability to control Sobolev functions, but for someone like me whose knowledge of { %katex } W^{1, p} { %endkatex } and  { %katex } L^1 { %katex } are pretty far apart, it's not particularly obvious. Potentially this is a gap in my knowledge I can fill with a lot of poring over something like [Measure Theory and Fine Properties of Functions](https://www.routledge.com/Measure-Theory-and-Fine-Properties-of-Functions-Revised-Edition/Evans-Gariepy/p/book/9781482242386) or something along those lines.

## C\#

The Sofware Guild has opened up a little course on C\# and .NET development. I've had experience in C\# before but not in this context. It looks like C\# itself is a nicer language than Java with more capabilities for functional programming. Pattern matching came around in like version 7 or 8 or something, which is wonderful. The documentation surrounding .NET is also nicer and more centralized compared to Java's sprawl all over odd websites. Best of all, the .NET documentation is by Microsoft which uses Segoe UI as its default font, which is my favorite sans-serif font.

I'm still not sure about the ecosystem surrounding .NET, however. Solution files and projects are a bit weird compared to a Maven project's "directory structure = package structure" and everything goes hard for the GUI paradigm (why does NuGet feel like an app store?). Most pressingly of all, Visual Studio for Mac is a huge steaming pile of poo. Luckily, I found out you can download early access versions of JetBrains Rider for free, a substantially better option considering I use pretty much every other JetBrains product. The C\# course also covers the IoC containers Ninject and Unity, both of which have ugly websites. Neither seem to be as "tentacles everywhere in your project" as Spring though, so I guess I can forgive them.

The language itself is cosy, a bit like a better Java. I never realized how extensive LINQ was - it's like a whole copy of SQL in C# itself. It might take some getting used to writing `Select` rather than `map`. Everything else seems to mostly be usual OOP stuff, with some glitter like class extensions and properties.

## Scala (and other functional programming)

I've never kept it a secret from my instructors that I'm fond of functional programming, though I'm not sure they think the same way. Presumably if you've been doing OOP for decades, you get quite comfortable with it. One instructor in particular is alright with having Java's lambdas be the extent of his functional programming expertise, though I like the idea of going much further with the paradigm. Recently, I've been focusing on Scala, since it has the usual functional benefits like a strong, static type system with higher-kinded type operators, pattern matching, typeclass patterns, and DSLs, as well as being part of the Java ecosystem, which is something I've grown fond of. Scala 3 is also on the horizon, but I'm not paying much attention to it at the moment since there's almost no documentation.

One of my troubles with functional programming is that it's difficult to find any good documentation on fully architecting a functional-first program with encapsulated side effects, loose coupling, immutability, purity, etc. As it stands, I can make something which is half-OOP, half-FP, such as an MVC thing where components are stuck in classes, but the business logic is all pure, and anything impure is encapsulated in IO or something (à la [this guessing game thing I made in like 20 minutes](https://github.com/Testyal/ScalaGuessingGame)). The resources that are available are scattered about (in contrast with OOP, where every website talks about abstract factories or whatever the big OO pattern is at the moment). There are a couple of books out there, like the Haskell-focused and prohibitively expensive [Functional Design and Architecture](https://leanpub.com/functional-design-and-architecture) and [Algebra-Driven Design](https://leanpub.com/algebra-driven-design), or the Scala based [Functional Programming in Scala](https://www.manning.com/books/functional-programming-in-scala), which is less focused on architecture but might provide a better entry point. There are also infinitely many blog posts about monads, monoids, magmas, and morphisms, which are wonderful and I love them very much - but how do I make something out of it?

Scala is also found more often in the industry than Haskell. Having a career involving Scala could provide a good balance between not being poor and genuinely using functional programming in something practical. 

## Japanese

Having effectively infinite free time now has allowed me to accelerate learning Japanese. At this point, I'm probably capable of passing N5 pretty comfortably, and I'm on my way through N4. Most of my time has been spent learning how to read above anything else. To that end, I've been focusing on learning the [Jōyō kanji](https://en.wikipedia.org/wiki/Jōyō_kanji) as a prerequisite (in no particular order, though the grade 1-4 ones I'm learning quicker because the vocabulary they're used in is more elementary). Three a day seems pretty appropriate - with this speed, I should be able to finish the Jōyō kanji in 2 years or so. At the minute I'm up to something like 250-300 kanji, and a couple hundred more words. 

My procedure diverts a little from the Genki textbook. I'm going through all the vocabulary I've learned so far in Genki I, taking the kanji I don't know and making funny physical flashcards out of them, which I revise daily. I have two kinds of vocabulary flashcards, the black type contains the Japanese + reading on the obverse and the definition on the reverse, and the red type contains just the Japanese on the obverse and the reading + definition on the reverse. If I encounter a word whose kanji I know, I make a black and red flashcard out of it.

Speaking of Genki, I've bought the second volume (having nearly finished the first). Normally, the textbook introduces me to an item of grammar, and I can then find the relevant item in my copy of [A Dictionary of Basic Japanese Grammar](https://www.tofugu.com/reviews/dictionary-of-basic-japanese-grammar/). All that happens then is basically the same thing I do when learning math: read through it slowly and paraphrase most of it (especially the example sentences) onto another bigger flashcard which I can revise from time to time. I've also consulted the dictionary for grammar I encounter outside the textbook (99% of the time on Twitter), like the たら and なら conditionals, the "although" words けれども、けれど、けども、けど, and the evidentials そうだ and そうだ.

Learning reading first provides a small base for everything else, but it also means I'm crap at everything else for now. A few weeks ago I was in an interview with someone from Nomura in London who asked me a question in Japanese which caught me by surprise, and I responded with the baby level dumb stupid 「私の日本語は悪いです」, when I should have responded 「私は日本語が下手です」. Hopefully that's not why they rejected me...

暇が無限にあるから私は日本語を勉強することを速めています。この時に私はN５の試験を出来るでしょう。今、N４を勉強しています。大抵読む練習をしますので常用漢字を覚えたいです。毎日３つの漢字の勉強はいいだと思うし、２年後常用漢字を覚え終わります。もう２５０〜３００覚えました。

私は勉強の仕方が「けんき」の教科書と違います。今はもう覚えた教科書の単語を読んでまだ覚えていない漢字を取って、毎日練習する紙のフラッシュカードを作っています。フラッシュカードは２タイプがあります。黒いカードは一方のサイドで日本語の単語とそれのひらがながあって、他方のサイドで英語の意味があります。赤いカードは一方のサイドで日本語の単語だけあって、他方のサイドでひらがなと英語の意味があります。私は漢字を知る単語を見たら黒いカードと赤いカードを作ります。

「げんき」は、第１本を読み終わるところので第２本を買いました。大抵教科書で文法を見て、「A Dictionary of Basic Japanese Grammar」という文法辞典にそれを見つけます。それから、文法の項目をゆっくり読んで、時々練習して単語のフラッシュカードより大きいカードに文法の項目をコピーします。教科書に見ない文法の項目も文法辞典に読んでいます。

聞いたり書いたり話したりする前に読む勉強は一番やさしいでしょうが、聞いたり書いたり話したりするが下手ですよ。数週間前、私は野村の仕事を面接していて面接者が日本語の質問を聞きました。私はびっくりので返事は「私の日本語は悪いです」だけれど「私は日本語が下手です」を返事したかったです。

私が書いた日本語を読んだならすみません。

## Anything else?

I finished [FF7 Remake](https://en.wikipedia.org/wiki/Final_Fantasy_VII_Remake) the other day. I never played the original or any other Final Fantasy besides FFXIV, so it was a nice introduction to the series and the characters. Hopefully the next one comes out soon, I wanna see Sephiroth again.
