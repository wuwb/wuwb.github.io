---
title: node.js 自然语言处理
date: 2019-11-24 20:36:46
tags:
---

## 介绍

互联网创造了大量非结构化文本数据。幸运的是，我们有现代的系统可以理解这类数据。

现代计算机系统可以使用称为 NLP（natural language processing）的基础技术来理解自然语言。 该技术可以将人类语言作为输入进行处理，并执行以下一项或多项操作：

- 情绪分析（是肯定还是否定的陈述？）
- 主题分类（关于什么？）
- 根据此声明确定应采取的措施
- 意图提取（此语句的意图是什么？

NLP 是语言学、计算机科学、信息工程和与计算机和人类自然语言之间的相互作用有关的人工智能，特别是如何对计算机进行编程以处理和分析大量自然语言数据。

由于我们的大多数设备都集成了AI（人工智能），ML（机器学习）和NLP以增强人机交互，因此，如今NLP的重要实现离我们也并不遥远。 以下是NLP运作中的一些常见示例：

- 搜索引擎：Google搜索引擎是最有用的技术之一。您输入文字并收到数百万个相关结果作为响应。由于NLP技术可以理解输入并执行一系列逻辑运算，因此这是可能的。这也是让Google搜索了解您的意图并在您拼写错误的搜索词时向您建议正确拼写的原因。
- 智能虚拟助手：Siri，Alexa和Google Assistant等虚拟助手显示了NLP实施的高级水平。在收到您的口头输入后，他们可以识别意图，执行操作并以自然语言发送回覆。
- 智能聊天机器人：聊天机器人可以分析大量文本数据，并根据大数据及其检测意图的能力给出不同的响应。这给人一种自然对话的整体感觉，而不是一台机器。
- 垃圾邮件过滤器：您是否注意到电子邮件客户端在将垃圾邮件从收件箱中过滤出来方面不断地变得越来越好？之所以可以这样做，是因为过滤器引擎可以理解电子邮件的内容（主要使用贝叶斯垃圾邮件过滤功能），并确定是否为垃圾邮件。

上面的用例表明，AI，ML和NLP已在网络上大量使用。 由于人类使用自然语言与网站进行交互，因此我们应该使用NLP功能来构建我们的网站。

当主题为NLP（或ML和AI）时，Python通常是首选语言，这是因为Python拥有丰富的语言处理包，例如Natural Language Toolkit。 但是，JavaScript迅速发展，并且NPM的存在为其开发人员提供了访问大量程序包的权限，其中包括用于执行不同语言的NLP的程序包。

在本文中，我们将重点介绍使用Node的NLP入门。 我们将使用一个称为natural的JavaScript库。 通过将自然库添加到我们的项目中，我们的代码将能够从用户输入中解析，解释，操纵和理解自然语言。

本文几乎不会涉及NLP的表面。 这篇文章对于已经在Python中使用NLP但希望过渡到Node来获得相同结果的开发人员而言非常有用。 完全的新手还将学到很多关于NLP作为一项技术及其在Node中的用法的知识。

## 预备

- Node.js 基础知识
- 可以运行 Node 代码的系统

## 安装

用下列命令安装 natural 包。

```
npm install natural
```

下列示例的代码可以在[github](https://github.com/Jordanirabor/nlp-node-natural-article)免费获取。

## 使用

下面介绍如何使用 natural 执行一些基础但是重要的 NLP 任务。

### Tokenization

Tokenization is the process of demarcating and possibly classifying sections of a string of input characters. The resulting tokens are then passed on to some other form of processing. The process can be considered a sub-task of parsing input.

For example, in the text string: The quick brown fox jumps over the lazy dog

The string isn’t implicitly segmented on spaces, as a natural language speaker would do. The raw input, the 43 characters, must be explicitly split into the 9 tokens with a given space delimiter (i.e., matching the string " " or regular expression /\s{1}/).

Natural ships with a number of smart tokenizer algorithms that can break text into arrays of tokens. Here’s a code snippet showing the usage of the Word tokenizer:

```
// index.js

var natural = require('natural');
var tokenizer = new natural.WordTokenizer();
```
console.log(tokenizer.tokenize("The quick brown fox jumps over the lazy dog"));
Running this with Node gives the following output:

```
[ 'The',
  'quick',
  'brown',
  'fox',
  'jumps',
  'over',
  'the',
  'lazy',
  'dog' ]
```

### Stemming

Stemming refers to the reduction of words to their word stem (also known as base or root form). For example, words such as cats, catlike, and catty will be stemmed down to the root word — cat.

Natural currently supports two stemming algorithms — Porter and Lancaster (Paice/Husk). Here’s a code snippet implementing stemming, using the Porter algorithm:

// index.js

var natural = require('natural');

natural.PorterStemmer.attach();
console.log("I can see that we are going to be friends".tokenizeAndStem());
This example uses the attach() method to patch stem() and tokenizeAndStem() to String as a shortcut to PorterStemmer.stem(token).tokenizeAndStem(). The result is the breaking down of the text into single words then an array of stemmed tokens will be returned:

[ 'go', 'friend' ]
Note: In the result above, stop words have been removed by the algorithm. Stop words are words that are filtered out before the processing of natural language(for example be, an, and to are all stop words).

Measuring the similarity between words (string distance)
Natural provides an implementation of four algorithms for calculating string distance, Hamming distance, Jaro-Winkler, Levenshtein distance, and Dice coefficient. Using these algorithms, we can tell if two strings match or not. For the sake of this project we will be using Hamming distance.

Hamming distance measures the distance between two strings of equal length by counting the number of different characters. The third parameter indicates whether the case should be ignored. By default, the algorithm is case sensitive.

Here’s a code snippet showing the usage of the Hemming algorithm for calculating string distance:

// index.js

var natural = require('natural');

console.log(natural.HammingDistance("karolin", "kathrin", false));
console.log(natural.HammingDistance("karolin", "kerstin", false));
console.log(natural.HammingDistance("short string", "longer string", false));
The output:

3
3
-1

The first two comparisons return 3 because three letters differ. The last one returns -1 because the lengths of the strings being compared are different.

### 分类

Text classification also known as text tagging is the process of classifying text into organized groups. That is, if we have a new unknown statement, our processing system can decide which category it fits in the most based on its content.

Some of the most common use cases for automatic text classification include the following:

Sentiment analysis

Topic detection
Language detection
Natural currently supports two classifiers — Naive Bayes and logistic regression. The following examples use the BayesClassifier class:

```
var natural = require('natural');

var classifier = new natural.BayesClassifier();
classifier.addDocument('i am long qqqq', 'buy');
classifier.addDocument('buy the q\'s', 'buy');
classifier.addDocument('short gold', 'sell');
classifier.addDocument('sell gold', 'sell');
classifier.train();

console.log(classifier.classify('i am short silver'));
console.log(classifier.classify('i am long copper'));
```

In the code above, we trained the classifier on sample text. It will use reasonable defaults to tokenize and stem the text. Based on the sample text, the console will log the following output:

```
sell
buy
```

### Sentiment analysis

Sentiment analysis (also known as opinion mining or emotion AI) refers to the use of natural language processing, text analysis, computational linguistics, and biometrics to systematically identify, extract, quantify, and study affective states and subjective information. Sentiment analysis is widely applied to voice of the customer materials such as reviews and survey responses, online and social media, and healthcare materials for applications that range from marketing to customer service to clinical medicine.

Natural supports algorithms that can calculate the sentiment of each piece of text by summing the polarity of each word and normalizing it with the length of the sentence. If a negation occurs the result is made negative.

Here’s an example of its usage:

// index.js

var natural = require('natural');
var Analyzer = natural.SentimentAnalyzer;
var stemmer = natural.PorterStemmer;
var analyzer = new Analyzer("English", stemmer, "afinn");

// getSentiment expects an array of strings
console.log(analyzer.getSentiment(["I", "don't", "want", "to", "play", "with", "you"]));
The constructor has three parameters:

Language
Stemmer- to increase the coverage of the sentiment analyzer a stemmer may be provided
Vocabulary- sets the type of vocabulary, "afinn", "senticon" or "pattern" are valid values
Running the code above gives the following output:

0.42857142857142855 // indicates a relatively negative statement
Phonetic matching
Using natural, we can compare two words that are spelled differently but sound similar using phonetic matching. Here’s an example using the metaphone.compare() method:

// index.js

var natural = require('natural');
var metaphone = natural.Metaphone;
var soundEx = natural.SoundEx;

var wordA = 'phonetics';
var wordB = 'fonetix';

if (metaphone.compare(wordA, wordB))
    console.log('They sound alike!');

// We can also obtain the raw phonetics of a word using process()
console.log(metaphone.process('phonetics'));
We also obtained the raw phonetics of a word using process(). We get the following output when we run the code above:

They sound alike!
FNTKS
Spell check
Users may make typographical errors when supplying input to a web application through a search bar or an input field. Natural has a probabilistic spellchecker that can suggest corrections for misspelled words using an array of tokens from a text corpus.

Let’s explore an example using an array of two words (also known as a corpus) for simplicity:

// index.js

var natural = require('natural');

var corpus = ['something', 'soothing'];
var spellcheck = new natural.Spellcheck(corpus);

console.log(spellcheck.getCorrections('soemthing', 1));
console.log(spellcheck.getCorrections('soemthing', 2));
It suggests corrections (sorted by probability in descending order) that are up to a maximum edit distance away from the input word. A maximum distance of 1 will cover 80% to 95% of spelling mistakes. After a distance of 2, it becomes very slow.

We get the following output from running the code:

[ 'something' ]
[ 'something', 'soothing' ]
Conclusion
Here’s a quick summary of what we’ve learned so far in this article:

Computer systems are getting smarter by the day and can extract meaning from large volumes of unstructured textual data using NLP
Python has a wealth of intelligent packages for performing AI, ML, and NLP tasks but JavaScript is growing really rapidly and its package manager has an impressive number of packages capable of processing natural language
Natural, a JavaScript package, is robust in performing NLP operations and has a number of algorithm alternatives for each task
The source code to each of the following usage examples in the next section is available on Github. Feel free to clone it, fork it or submit an issue.

## 其他
Find more information on this topic via the following links:

What is Natural Language Processing and why it matters
AI basics- Natural Language Processing with Node
Natural Language Processing and Machine Learning in JavaScript
What is Text Classification?

## 参考

- https://blog.logrocket.com/natural-language-processing-for-node-js/
- https://github.com/Jordanirabor/nlp-node-natural-article
