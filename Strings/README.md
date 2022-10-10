# String
## Character

There is more than one possible way of encoding characters, but only some of them gained worldwide popularity and are commonly used in IT: these are 
- ASCII (used mainly to encode the Latin alphabet and some of its derivates)
- UNICODE (able to encode virtually all alphabets being used by humans).

**1. ASCII**

 ASCII (short for American Standard Code for Information Interchange) is the most widely used, and you can assume that nearly all modern devices (like computers, printers, mobile phones, tablets, etc.) use that code.

A classic form of ASCII code uses eight bits for each sign. Eight bits mean 256 different characters. 

- The first 128 are used for the standard Latin alphabet (both upper-case and lower-case characters).
- The remaining 128 were set for different languages by codepage.

**2. codepoint**

A code point is a number which makes a character. 

**3. codepage**

A code page is a standard for using the upper 128 code points to store specific national characters.

For example, the code point 200 makes Č (a letter used by some Slavic languages) when utilized by the ISO/IEC 8859-2 code page, and makes Ш (a Cyrillic letter) when used by the ISO/IEC 8859-5 code page.

**4. Unicode**

- Unicode assigns unique (unambiguous) characters (letters, hyphens, ideograms, etc.) to more than a million code points.

- The Unicode standard says nothing about how to code and store the characters in the memory and files. 

- There is more than one standard describing the techniques used to implement Unicode in actual computers and computer storage systems. The most general of them is UCS-4.

**5. UCS-4(Universal Character Set)**

- UCS-4 uses 32 bits (four bytes) to store each character, and the code is just the Unicode code points' unique number.

- A file containing UCS-4 encoded text may start with a BOM (byte order mark), an unprintable combination of bits announcing the nature of the file's contents. 

- As you can see, UCS-4 is a rather wasteful standard - it increases a text's size by four times compared to standard ASCII. 

**6. UTF-8(Unicode Transformation Format)**

The concept is very smart. UTF-8 uses as many bits for each of the code points as it really needs to represent them.

## Nature of String

Python's strings are immutable sequences.

**1. concatenated(+)**

**2. replicated**

```python
str1 = 'a'
str2 = 'b'

print(str1 + str2) #output : ab
print(str2 + str1) #output : ba
print(5 * 'a') #output : aaaaa
print('b' * 4) #output : bbbb
```

**3. ord()**

The function takes a character and returns its code point.
```python
char_1 = 'a'
char_2 = ' '  # space

print(ord(char_1)) #output : 97
print(ord(char_2)) $ output : 32
```
**4. char()**

The function takes a code point and returns its character.
```python
print(chr(97)) #output : a
print(chr(945)) #output: α
```

**5. indexing**
```python
# Indexing strings.

the_string = 'silly walks'

for ix in range(len(the_string)):
    print(the_string[ix], end=' ') # output : s i l l y   w a l k s 
```

**6. iterating**
```python
# Iterating through a string.

the_string = 'silly walks'

for character in the_string:
    print(character, end=' ') # output: s i l l y   w a l k s
```

**7. Slices**
```python
# Slices

alpha = "abdefg"

print(alpha[1:3]) #output: bd
print(alpha[3:]) #output: efg
print(alpha[:3]) #output: abd
print(alpha[3:-2]) #output: e
print(alpha[-3:4]) #output: e
print(alpha[::2]) #output: adf
print(alpha[1::2]) #output: beg
```

**8. in and not in**

It simply checks if its left argument (a string) can be found anywhere within the right argument (another string).
```python
alphabet = "abcdefghijklmnopqrstuvwxyz"

print("f" in alphabet) #output: True
print("F" in alphabet) #output: False
print("1" not in alphabet) #output: True
print("ghi" not in alphabet) #output: False
print("Xyz" not in alphabet) #output: True
```

**9. min()**

The function finds the character with the minimal codepoint.

```python
# Demonstrating min() - Example 1:
print(min("aAbByYzZ")) #output: A

# Demonstrating min() - Examples 2 & 3:
t = 'The Knights Who Say "Ni!"'
print('[' + min(t) + ']') #output: [ ]

t = [0, 1, 2]
print(min(t)) #output: 0
```

**Note:**

-  The sequence cannot be empty, or else you'll get a ValueError exception.

**10. max()**

The function finds the character with the maximal codepoint.
```python
# Demonstrating max() - Example 1:
print(max("aAbByYzZ")) #output: z

# Demonstrating max() - Examples 2 & 3:
t = 'The Knights Who Say "Ni!"'
print('[' + max(t) + ']') #output: [y]

t = [0, 1, 2]
print(max(t)) #output:2
```

**11. index()**

The method returns the index of the first occurrence of the argument.
```python
# Demonstrating the index() method:
print("aAbByYzZaA".index("b")) #output: 2
print("aAbByYzZaA".index("Z")) #output: 7
print("aAbByYzZaA".index("A")) #output: 1
```

**Note:**

- The element searched for must occur in the sequence - its absence will cause a ValueError exception.

**12. list()**

The list() function create a list consisting of all the string's characters.
```python
# Demonstrating the list() function:
print(list("abcabc")) #output: ['a', 'b', 'c', 'a', 'b', 'c']
```

**13. count()**

The count() method counts all occurrences of the element inside the sequence.
```python
# Demonstrating the count() method:
print("abcabc".count("b")) #output: 2
print('abcabc'.count("d")) #output: 0
```

## String methods
- capitalize() – changes all string letters to capitals;
```python
# Demonstrating the capitalize() method:
print("Alpha".capitalize()) #output: Alpha
print('ALPHA'.capitalize()) #output: Alpha
print(' Alpha'.capitalize()) #output: ' alpha'
print('123'.capitalize()) #output: 123
print("αβγδ".capitalize()) #output: Αβγδ
```

    **Note**:

    - if the first character inside the string is a letter,it will be converted to upper-case;
    - all remaining letters from the string will be converted to lower-case.

- center() – centers the string inside the field of a known length;
```python
# Demonstrating the center() method:
print('[' + 'Beta'.center(2) + ']') #output:[Beta]
print('[' + 'Beta'.center(4) + ']') #output:[Beta]
print('[' + 'Beta'.center(6) + ']') #output:[ Beta ]
print('[' + 'gamma'.center(20, '*') + ']') #output:[*******gamma********]
```

    **Note:**

    - The two-parameter variant of center() makes use of the character from the second argument, instead of a space.
    - If the target field's length is too small to fit the string, the original string is returned.
    
- endswith() – does the string end with a given substring?
```python
t = "zeta"
print(t.endswith("a")) #output:True
print(t.endswith("A")) #output:False
print(t.endswith("et")) #output:False
print(t.endswith("eta")) #output:True
```

- find() - it looks for a substring and returns the index of first occurrence of this substring.
```python
# Demonstrating the find() method:
print("Eta".find("ta")) #output:1
print("Eta".find("mma")) #output:-1
print('kappa'.find('a', 2)) #output:4
```

    **Note:**
    - it doesn't generate an error for an argument containing a non-existent substring (it returns -1 then)
    - it works with strings only - don't try to apply it to any other sequence.
    - The second argument specifies the index at which the search will be started

- isalnum() - does the string consist only of letters and digits?
```python
# Demonstrating the isalnum() method:
print('lambda30'.isalnum()) #output: True
print('lambda'.isalnum()) #output: True
print('30'.isalnum()) #output: True
print('@'.isalnum()) #output: False
print('lambda_30'.isalnum()) #output: False
print(''.isalnum()) #output: False

```
- isalpha() – does the string consists only of letters?
- isdigit() - does the string consists only of digits?

```python
# Example 1: Demonstrating the isapha() method:
print("Moooo".isalpha()) #output:True
print('Mu40'.isalpha()) #output:Trus

# Example 2: Demonstrating the isdigit() method:
print('2018'.isdigit()) #output:True
print("Year2019".isdigit()) #output:False
```

- islower() – does the string consists only of lower-case
- isupper() – does the string consists only of upper-case letters?
- isspace() – does the string consists only of white spaces?
```python
# Example 1: Demonstrating the islower() method:
print("Moooo".islower()) #output: False
print('moooo'.islower()) #output: True

# Example 2: Demonstrating the isspace() method:
print(' \n '.isspace()) #output: True
print(" ".isspace()) #output: True
print("mooo mooo mooo".isspace()) #output: False

# Example 3: Demonstrating the isupper() method:
print("Moooo".isupper()) #output: False
print('moooo'.isupper()) #output: False
print('MOOOO'.isupper()) #output: True
```
- join() – joins all items of a tuple/list into one string;
```python
# Demonstrating the join() method:
print(",".join(["omicron", "pi", "rho"])) #output:omicron,pi,rho
```

- lower()  – converts all the string's letters into lower-case letters;
```python
# Demonstrating the lower() method:
print("SiGmA=60".lower()) #output:sigma=60
```

- lstrip() – removes the white characters from the beginning of the string;
```python
# Demonstrating the lstrip() method:
print("[" + " tau ".lstrip() + "]") #output:[tau ]
print("www.cisco.com".lstrip("w.")) #output:cisco.com
print("pythoninstitute.org".lstrip(".org")) #output:pythoninstitute.org
```

    **Note:**

    - The argument is not a prefix; rather, all combinations of its values are stripped.
    
- replace() – replaces a given substring with another;
```python
# Demonstrating the replace() method:
print("www.netacad.com".replace("netacad.com", "pythoninstitute.org")) #output:www.pythoninstitute.org
print("This is it!".replace("is", "are")) #output:Thare are it!
print("Apple juice".replace("juice", "")) #output:Apple
print("This is it!".replace("is", "are", 1)) #output:Thare is it!
print("This is it!".replace("is", "are", 2)) #output:Thare are it!
```

    **Note:**

    - The two-parameter replace() method returns a copy of the original string in which all occurrences of the first argument have been replaced by the second argument.
    - The three-parameter replace() variant uses the third argument (a number) to limit the number of replacements.

- rfind()  – finds a substring starting from the end of the string;
```python
# Demonstrating the rfind() method:
print("tau tau tau".rfind("ta")) #output:8
print("tau tau tau".rfind("ta", 9)) #output:-1
print("tau tau tau".rfind("ta", 3, 9)) #output:4
```
- rstrip() – removes the trailing white spaces from the end of the string;
```python
# Demonstrating the rstrip() method:
print("[" + " upsilon ".rstrip() + "]") #output:[ upsilon]
print("cisco.com".rstrip(".com")) #output:cis
```

- split() – splits the string into a substring using a given delimiter;
```python
# Demonstrating the split() method:
print("phi       chi\npsi".split()) #output:['phi', 'chi', 'psi']
```

- startswith() – does the string begin with a given substring?
- strip() – removes the leading and trailing white spaces;
```python
# Demonstrating the startswith() method:
print("omega".startswith("meg")) #output:False
print("omega".startswith("om")) #output:True

# Demonstrating the strip() method:
print("[" + "   aleph   ".strip() + "]") #output:[aleph]
```

- swapcase()  – swaps the letters' cases (lower to upper and vice versa)
- title()  – makes the first letter in each word upper-case;
- upper() – converts all the string's letter into upper-case letters.
```python
# Demonstrating the swapcase() method:
print("I know that I know nothing.".swapcase()) #output:i KNOW THAT i KNOW NOTHING.

# Demonstrating the title() method:
print("I know that I know nothing. Part 1.".title()) #output:I Know That I Know Nothing. Part 1.

# Demonstrating the upper() method:
print("I know that I know nothing. Part 2.".upper()) #output:I KNOW THAT I KNOW NOTHING. PART 2.
```









