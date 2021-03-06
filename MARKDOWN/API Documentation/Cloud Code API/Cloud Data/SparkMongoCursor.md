---
src: /API Documentation/Cloud Code API/Cloud Data/SparkMongoCursor.md
---

# SparkMongoCursor

An iterator over database results. Doing a find() query on a collection returns a SparkMongoCursor thus:

<pre rel="highlighter" code-brush="js" contenteditable="false">var cursor = collection.find( query );</br>if( cursor.hasNext() ) </br>{var obj = cursor.next();}</pre>

Warning: Calling toArray() on a SparkMongoCursor will irrevocably turn it into an array. This means that, if the cursor was iterating over ten million results (which it was lazily fetching from the database), suddenly there will be a ten-million element array in memory. Before converting to an array, make sure that there are a reasonable number of results using skip() and limit().

For example, to get an array of the 1000-1100th elements of a cursor, use

<pre rel="highlighter" code-brush="js" contenteditable="false">var obj = collection.find( query ).skip( 1000 ).limit( 100 ).toArray();</pre>

e.g.

<pre rel="highlighter" code-brush="js" contenteditable="false">var myMetaCollection = Spark.runtimeCollection('metatest');</pre>


## limit
_signature_ limit(number count)</p>
_returns_ [SparkMongoCursor](/API Documentation/Cloud Code API/Cloud Data/SparkMongoCursor.md)</p>
Limits the number of elements returned.
<b>params</b>
count - the limit to set
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var obj = collection.find( query ).skip( 1000 ).limit( 100 ).toArray();</pre>

## skip
_signature_ skip(number count)</p>
_returns_ [SparkMongoCursor](/API Documentation/Cloud Code API/Cloud Data/SparkMongoCursor.md)</p>
Discards a given number of elements at the beginning of the cursor.
<b>params</b>
count - the limit to set
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var obj = collection.find( query ).skip( 1000 ).limit( 100 ).toArray();</pre>

## size
_signature_ size()</p>
_returns_ number</p>
Counts the number of objects matching the query this does take limit/skip into consideration.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var size = collection.find( query ).size();</pre>

## count
_signature_ count()</p>
_returns_ number</p>
Counts the number of objects matching the query this does take limit/skip into consideration.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var count = collection.find( query ).count();</pre>

## sort
_signature_ sort(JSON orderBy)</p>
_returns_ [SparkMongoCursor](/API Documentation/Cloud Code API/Cloud Data/SparkMongoCursor.md)</p>
Sorts this cursor's elements. This method must be called before getting any object from the cursor.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var obj = collection.find( query ).sort( {"field" : 1} ).limit( 100 ).toArray();</pre>

## hasNext
_signature_ hasNext()</p>
_returns_ boolean</p>
Checks if there is another object available.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var cursor = collection.find( query ); if( cursor.hasNext() ) {var obj = cursor.next();}</pre>

## next
_signature_ next()</p>
_returns_ JSON</p>
Returns the object the cursor is at and moves the cursor ahead by one.
<b>returns</b>
a JSON object
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var cursor = collection.find( query ); if( cursor.hasNext() ) {var obj = cursor.next();}</pre>

## curr
_signature_ curr()</p>
_returns_ JSON</p>
Returns the element the cursor is at.
<b>returns</b>
a JSON object
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var cursor = collection.find( query ); if( cursor.hasNext() ) {cursor.next(); var obj = cursor.curr();}</pre>

