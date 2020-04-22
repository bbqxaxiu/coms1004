# Exceptions

***Checked vs. Unchecked Exceptions***

 -  A "checked" exception is checked during compile time while as an "unchecked" exception is not. Specifically, what this means is checked exceptions must be handled adequately before your program is allowed to compile but the same does not go for unchecked exceptions (i.e. your program will still compile even if you do not handle unchecked exceptions adequately). 
 
    - Here, checked exceptions are shown in red and unchecked exceptions are shown in blue. 
    ![alt text](https://cdn2.howtodoinjava.com/wp-content/uploads/ExceptionHierarchyJava.png?style=centerme)

 -  Checked exceptions are typically out of the programmer's control. For example, an IOException is thrown when an error occurs with the reading/writing of a file (the file you are trying to read does not exist, you do not have permission to read the file, etc). Unchecked exceptions, on the other hand, are typically the fault of the programmer. For example, an IndexOutOfBoundsException is thrown when the programmer does not manipulate/handle Arrays correctly. 

<br>

***Handling Checked vs. Unchecked Exceptions***

 - If a method may throw a checked exception, you must either 1) catch it using a ***try/catch block*** or 2) declare that the method throws the exception using the ***throws*** key word. 

 
 Take the following example: 
 
    import java.util.*;
    import java.io.*;
    
    public class Example {
    
      public static void main(String[] args) {
        File file = new File(args[0]);
        BufferedReader br = new BufferedReader(new FileReader(file));
    
        String str;
        while((str = br.readLine()) != null) {
          System.out.println(str);
        }
      }
    }

This program uses the File, FileReader, and BufferedReader libraries to print out every line of a file specified in the command line. To run it, we would call `javac Example.java` then `java Example [name of file]`. However, when we try to compile this program, we get the following error: 

```
dyn-160-39-9-141:Desktop nhudoan$ javac Example.java
Example.java:8: error: unreported exception FileNotFoundException; must be caught or declared to be thrown
    BufferedReader br = new BufferedReader(new FileReader(file));
                                            ^
Example.java:11: error: unreported exception IOException; must be caught or declared to be thrown
    while((str = br.readLine()) != null) {
                            ^
``` 

The reason for this is because FileReader and BufferedReader throw a FileNotFoundException and an IOException, both of which are checked exceptions, when a file does not exist in the same repository or when there is a problem with reading from the file, respectively. The compiler generates this warning because we have written a method that throws a checked exception but we have not done one of 1) catching it with a ***try/catch block*** or 2) declaring that the method throws the exception using the ***throws*** key word. 

To fix this, we can either catch the exception, like this: 

```
import java.util.*;
import java.io.*;

public class Example {
  public static void main(String[] args) {
    try {
      File file = new File(args[0]);
      BufferedReader br = new BufferedReader(new FileReader(file));

      String str;
      while((str = br.readLine()) != null) {
        System.out.println(str);
      }
    } catch (FileNotFoundException e) {
      System.out.println("The file does not exist.");
    } catch (IOException e) {
      System.out.println("There was a problem with reading from the file.");
    }
  }
}
```

Or we can declare that the method throws the two checked exceptions in the method header, like this: 

```
import java.util.*;
import java.io.*;

public class Example {
  public static void main(String[] args) throws IOException, FileNotFoundException {
    File file = new File(args[0]);
    BufferedReader br = new BufferedReader(new FileReader(file));

    String str;
    while((str = br.readLine()) != null) {
      System.out.println(str);
    }
  }
}
```

Note that while adding the ***throws*** clause allows the program to compile, it is generally not good practice to do this in the main method, where the exception cannot be caught elsewhere. (You would typically only do this within a method that the main method calls on, where the ***throws*** key word ensures the checked exception is then percolated up to the main method where it can then be caught). 

Note: the .readLine() method of the BufferedReader class, which you will find helpful in your programming project, skips to the next line of the file every time it is called. So in this case, at every iteration of the while loop we are resetting what str equals to the next line of the file (which will be read in as a String). We stop when we notice that what we've read in is null (i.e. we are at the end of the file). 




Take the following example: 
```
import java.util.*;
import java.io.*;

public class Example {
  public static void main(String[] args) {
    int x = 0;
    int y = 3;

    System.out.println(y/x); 
  }
}
```

If we run this code, it compiles but during runtime we get the following error: 
```
dyn-160-39-9-141:Desktop nhudoan$ java Example
Exception in thread "main" java.lang.ArithmeticException: / by zero
        at Example.main(Example.java:10)
```
ArithmeticException is an example of an unchecked exception (i.e. the fault of the programmer). If anything you in your methods throws a checked exception, it is up to you to properly catch it so that your program terminates gracefully. We will take off points for programs that do not terminate gracefully and display a stack trace when an unchecked exception is thrown. 
