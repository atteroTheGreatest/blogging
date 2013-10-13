---
layout: post
title: "Fitting text into categories"
date: 2013-05-19 20:05
comments: true
categories: programming, scala, nlp
---

### How to classify?
You can use various methods to classify objects. There are many tools in machine learning and natural language processing packages. But sometimes it's hard to find one, which suits your problem well. I wanted to write category classifier in scala, making it as simple as possible. I could use [breeze](http://www.scalanlp.org/), but at first glance it's quite overwhelming and documentation isn't really user friendly. (I love python [scikit-learn](http://scikit-learn.org/stable/), which is in my opinion the best machine learning library in the world)

I decided to implement it all by myself using only basic SDK of scala. 

### Main idea behind my script
In written language exist lots of common words such as: "the", "and", "this", etc. Specialised article or book contains lots of vocabulary connected to the field.

I did some web crawling to collect some articles with typical vocabulary for three basic fields: physics, electronics and mathematics. As a sample of normaly used vocabulary (not conected with any specialised field) I used some random articles from Guardian. 

After collecting articles I could compute the most common worlds for each category. My classifying algorithm basically chooses a category, which vocabulary has the biggest intersection with given text, if intersection is very small it returns category "boring".

### Implementation 
{% codeblock splitContentToSentences - commonVocabulary.scala %}
import java.io.RandomAccessFile
import scala.collection.mutable.HashMap

def removePunctuation(text: String) = {
	val punct = ",.?;:!\""
	text.toList.filterNot(char => punct contains char).mkString("")
}

def getWordsFromRawText(text: String) = {
	removePunctuation(text).toLowerCase.split("\\s+").toList
}

def getAllWords(basePath: String) = {
	import java.io.File
	val baseDir = new File(basePath)
	val paths = baseDir.listFiles.toList.sorted
	var words = List[String]()
	for( path <- paths) {
		val raf = new RandomAccessFile(path, "r")
		val buff = new Array[Byte](raf.length.toInt)
		raf.readFully(buff)
		words = words ++: getWordsFromRawText(new String(buff))
	}
	words
}

def rankWords(words: List[String], normalVocabulary: Set[String]) = {
	var wordOccurences = new HashMap[String, Int]()
	for(word <- words if !( normalVocabulary contains word) ){
		if (wordOccurences contains word) {
			wordOccurences(word) += 1
		}
		else
			wordOccurences(word) = 1
	}
	wordOccurences.toList.sortBy(_._2).reverse
}

val basePath = "articles/physics/"
val normalVocabulary = getAllWords("articles/random/")


val commonNormalVoc = (for {word <- 
	rankWords(normalVocabulary, Set("")).slice(0, 400)}
	 yield word._1).toSet

val physicsVocabulary = getAllWords("articles/physics/")
val commonPhysicsVoc = (for {word <- rankWords(physicsVocabulary, 
	commonNormalVoc).slice(0, 400)} yield word._1).toSet

val electronicsVocabulary = getAllWords("articles/electronics/")
val commonElectronicsVoc = (for {word <- 
	rankWords(electronicsVocabulary, 
	commonNormalVoc).slice(0, 400)} yield word._1).toSet

val mathVocabulary = getAllWords("articles/math/")
val commonMathVoc = (for {word <- rankWords(mathVocabulary,
 commonNormalVoc).slice(0, 400)} yield word._1).toSet

val testArticleAboutPhysics = """
Thermodynamics is a branch of natural science 
concerned (...) or statistical mechanics, gave
 explanations of macroscopic thermodynamics by 
 statistical predictions of the collective motion 
 of particles based on the mechanics of their 
 microscopic behavior.
"""

val testArticleAboutMath = """
Algebra can essentially be considered 
as doing computations (...) a polynomial 
in a single variable.
"""

val testArticleAboutElectronics = """
Wheatstone bridge
(...) zero the voltage.
"""

val typicalGuardianArticle = """
The French president, (...) have legalised same-sex marriage.
"""

def matchCategory(text: String) = {
	val words = getWordsFromRawText(text).toSet
	val wordsCount = words.size
	val categories =  HashMap("physics" ->
	 (words intersect commonPhysicsVoc).size.toDouble / 
	 wordsCount * 100,
	"electronics" -> (words intersect commonElectronicsVoc).size.toDouble 
	/ wordsCount * 100,
	"math" -> (words intersect commonMathVoc).size.toDouble /
	 wordsCount * 100).toList.sortBy(_._2).reverse
	
	val winningCategory = if (categories(0)._2 > 10)
	 categories(0) 
	else 
		("boring", (words intersect commonNormalVoc).size.toDouble
		 / wordsCount * 100)
	println("Article matches category: " + winningCategory)
	println(categories)
	println("Similarity to normal vocabulary: " +
	 (words intersect commonNormalVoc).size.toDouble 
	 / wordsCount * 100)
}

println("Testing article about physics:")
matchCategory(testArticleAboutPhysics)
println("\nTesting article about math:")
matchCategory(testArticleAboutMath)
println("\nTesting article about electronics:")
matchCategory(testArticleAboutElectronics)
println("\nTesting typical guardian article:")
matchCategory(typicalGuardianArticle)
{% endcodeblock %}

I stored collected articles in directory "articles/{category}" and used them to generate vocabulary sets.

There are two important functions in this code: "rankWords" and "match category". Ranking is based of how many times given word occurs in the text. Matching categories using set intersections to estimate which category suits the best.

Here is the output of this script (test files were much longer):

{% codeblock commonVocabulary.scala output%}
Testing article about physics:
Article matches category: (physics,34.66666666666667)
List((physics,34.66666666666667), (electronics,10.222222222222223), (math,8.0))
Similarity to normal vocabulary: 23.11111111111111

Testing article about math:
Article matches category: (math,26.01880877742947)
List((math,26.01880877742947), (physics,21.003134796238246), (electronics,13.793103448275861))
Similarity to normal vocabulary: 23.824451410658305

Testing article about electronics:
Article matches category: (electronics,23.717948717948715)
List((electronics,23.717948717948715), (physics,16.666666666666664), (math,14.102564102564102))
Similarity to normal vocabulary: 27.564102564102566

Testing typical guardian article:
Article matches category: (boring,30.45977011494253)
List((electronics,2.8735632183908044), (math,2.2988505747126435), (physics,2.2988505747126435))
Similarity to normal vocabulary: 30.45977011494253

{% endcodeblock %}


It took some code, but it's actually pretty simple and works well. Scala offers really nice api to work with this kind of problems.