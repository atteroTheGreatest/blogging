---
layout: post
title: "Reading With Preon"
date: 2013-05-08 16:00
comments: true
categories: 
---

###A... what?
Preon is a Java library which aims to provide a framework for dealing with binary encoded data. [Repository](https://github.com/preon/preon)

Actually reading binary files in Java isn't very comfortable. I love a python way to deal with binary files - [struct](http://docs.python.org/2/library/struct.html)

{% codeblock lang:python %}
	import struct


	#How exemplary data is packed
	format = "<IIH2s"

	#How long it is
	how_many_bytes = calcsize(format)

	#unpacking
	something = struct.unpack(format, string_with_binary_data)

	#packing
	packed =  pack('llh0l', 1, 2, 3)

{% endcodeblock %}

Nice and clean. What about Java? There are many ways to read binary files with Java. Almost all are very tedious. I decided to use preon. [Here](http://www.scribd.com/doc/8128172/Preon-Introduction) and [there](http://www.scribd.com/doc/7988375/Preon-Under-the-Hood) you can read some publications about preon.

###How to use preon?
I think that from user point of view, the most important part of preon library are codecs.


{% codeblock lang:java%}
//Create codec based on previously defined class
	Codec<EXTHHeader> codec = Codecs.create(EXTHHeader.class);
//Create buffer with data to be read
	RandomAccessFile fp = new RandomAccessFile(file, "r");
	fp.seek(offset);
	byte[] buff= new  byte[headers.size];
	fp.read(buff, 0, headers.exthHeaderSize);
//Decode your object from buffer
	EXTHHeader exthHeader = Codecs.decode(codec, buff);
{% endcodeblock %}


{% codeblock lang:java%}
import nl.flotsam.preon.annotation.BoundNumber;
//There is something like big and little endian (default is little)
import nl.flotsam.preon.buffer.ByteOrder;


public class EXTHHeader {
	//I use long with size 32 to represent unsigned 32 bit int
	//Reading signed int is identical except from using int instead of long
    @BoundNumber(size="32", byteOrder=ByteOrder.BigEndian)
    long identifier;
    @BoundNumber(size="32", byteOrder=ByteOrder.BigEndian)
    long headerLength;
    @BoundNumber(size="32", byteOrder=ByteOrder.BigEndian)
    long recordCount;
    
	@Override
	public String toString() {
		return "EXTHHeader [identifier=" + identifier + ", headerLength="
				+ headerLength + ", recordCount=" + recordCount + "]";
	}
  
}
{% endcodeblock %}

You can define byte order, size, type... and even lists with size based on value from one of fields. You can also add different methods to class (like toString).

I forgot to mention, Preon has lots of dependencies, you have to include them in your project or it won't work.

Not so hard, isn't it? And it has lot's more functionalities, but those above are the most common ones.

