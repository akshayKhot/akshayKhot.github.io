---
layout: post
title: How Base64 Encoding Works
tags: random
---

When programming, it's easy to get by with a superficial understanding of many things. You can easily fool yourself by thinking that you are programming when you are blindly copy+pasting Stack Overflow answers. 

Base64 encoding was one of these topics that was bugging me for a while. I often came across Base64 data, such as Base64 encoded image or URL, and had no idea whatsoever it meant or why it was even used. Finally, I decided to do some research to fill that knowledge gap. Here's what I learned.

<div class="random centered">
  <a target="_blank" href="{{site.photos}}/base64_encoding.png">
    <img src="{{site.photos}}/base64_encoding.png" alt="Base64 Encoding">
  </a>
  <div class="caption">Base64 Alphabet</div>
</div>

Base64 encoding takes binary data and converts it into text, specifically ASCII text. The resulting text contains only letters from `A-Z`, `a-z`, numbers from `0-9`, and the symbols `+` and `/`. As there are 26 letters in the alphabet, we have `26 + 26 + 10 + 2 = 64` characters, hence the name Base64.  

As there are only 64 characters available to encode into, we can represent them using only 6 bits because `2^6 = 64`. Every Base64 digit represents 6 bits of data. There are 8 bits in a byte, and the closest common multiple of 8 and 6 is 24. So 24 bits, or 3 bytes, can be represented using 4 6-bit Base64 digits. For example, the text

```c
My name is Akshay
```

can be encoded as a Base64 string 

```c
TXkgbmFtZSBpcyBBa3NoYXk=
```

The next question is why do we do this encoding. The most obvious use case is when we have to transmit some binary data over the network that's supposed to handle text. Base64 can also be used for passing data in URLs when that data includes non-URL friendly characters.

That is all well and good, but how do you actually convert data to Base64? Here's a simple algorithm that converts some text into Base64:

1. Convert the text to its binary representation. 
2. Divide the bits into groups of 6 bits each.
3. Convert each group to a decimal number from 0-63. It cannot be greater than 64 as there are only 6 bits in each group. 
4. Convert this decimal number to the equivalent Base64 character using the Base 64 alphabet. 

That's it. You have a Base64 encoded string. If there're insufficient bits in the final group, you can use '=' or '==' as padding. 

Here's an example that converts my name "Akshay" to its Base64 equivalent string. 

- Convert "Akshay" to binary, which looks like:

```c
01000001 01101011 01110011 01101000 01100001 01111001
```

- Divide the bits into groups of 6 bits in a group, instead of 8 bits

```c
010000 010110 101101 110011 011010 000110 000101 111001
```

- Convert each group to a decimal number

```c
16 22 45 51 26 6 5 57
```

- Now use the above Base 64 alphabet to convert each group to its Base 64 representation.

```c
QWtzaGF5
```

Here is a program in C# that takes some text as input and converts it into Base-64 encoded string.

```c#
public static string ToBase64(string value)
{
    byte[] bytes = Encoding.ASCII.GetBytes(value);

    string base64 = Convert.ToBase64String(bytes);

    return base64;
}
```

For more information, see the [RFC ](https://tools.ietf.org/html/rfc4648)for Base64, which describes the encoding in detail. 