# char vs. String

***char vs. String: basic differences***
 -  char (not capitalized) is one of the 8 Java primitive types, along with boolean, integer, float, long, and so on. Primitive types are built-in to Java, and serve as the basis of data manipulation.

 -  String is an actual class in the Java library, meaning if you go online and read Java docs you can see how the class is laid out (and how the makers of Java, i.e. Oracle) defined how it should work.

	 - Java Documentation

		 - https://docs.oracle.com/javase/7/docs/api/java/lang/String.html?is-external=true
		 - [https://docs.oracle.com/javase/7/docs/api/](https://docs.oracle.com/javase/7/docs/api/) (other familiar classes, e.g. Scanner, are here!)

***char vs. String: creation***

 - To create a char, you use single quotes.
	 - `char myCharacter = 'A'`

 -  To create a String, you use double quotes.
	 - `String myString = "A"`

***char vs. String: comparison***
 -  To compare a String to a String, you use .equals()
	 - `"T".equals("T") //returns true`
	 - `"T".equals('T') //returns false`

 -  To compare a char to a char, you use ==
	 - `'T' == 'T'`
	 - ASCII: encodes every char to an integer.
	 	- `'a' == 97 //returns true`

 - .equals() vs. ==
	- .equals() is a method (check the Java docs for the String class) while as == is an operator.
	- The String class defines the .equals() method for comparison between two Strings. In the same way, you define a .equals() method for any class you create (and decide what conditions are used to evaluate equality).
	- The == operator is used for comparison between two primitive types (as well as object references).


 # String Manipulation

 - Useful Methods for String Manipulation that you can use in
   Programming Project 2:

	 -   String.replace()

	 -   String.charAt()

	 -   String.substring()

	 -   String.length()

	 -   Character.getNumericValue()

	 -   Integer.parseInt()

   You may notice the "Character" and "Integer" key words used here. Character, Integer, Long, etc. are what we call "wrapper classes" in Java. They were created and "wrap around" their corresponding primitive type (i.e. Character to char, Integer to int, Long to long, and so on) and allow us to better manipulate/give more functionality to the Java primitive types.

 - Resources

	-   [https://www.tutorialspoint.com/java/java_strings.htm](https://www.tutorialspoint.com/java/java_strings.htm)

	-   [https://www.tutorialspoint.com/java/lang/java_lang_integer.htm](https://www.tutorialspoint.com/java/lang/java_lang_integer.htm)
