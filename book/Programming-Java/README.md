## Knowledge Base for Java Programming Language
* Book
  - Thinking in Java 4th ed (Bruce Eckel)
  - [I'm an inline-style link](https://www.google.com)
* Book Notes
  - Coding style: `camel-casing`
  - **if-else** operator: `boolean-exp ? vale0 : value1`
  - Casting: Allows to cast any primitive type to any other primitive type,
    except **boolean**. Class types do not allow casting. Promotion.
  - *A compendium of operators*: Book page 84-90.
  - **if-else**
      ```java
        if (testval > target)
           result = +1;
        else if (testval <target)
           result = -1;
        else
           result = 0; // Match
        ```
  - **Iteration**
      ```java
      while(boolean-exp)
        statement

      do
         statement
      while(boolean-exp)

      for (initialization; boolean-exp; step)
        statement
      for (char c = 0; c < 128; c++) {}
      //Using the comma operator, you can define multiple variables within a for
      //statement, but they must be of the same type
      for (int i=1, j=i+10; i< 5; i++, j=i*2) {}
        /* output:
        i = 1 j= 11
        i = 2 j = 4
        i = 3 j = 6
        i = 4 j = 8
        */
      // Java SE5 introduces new for syntax, for use with arrays and containers.
      // This is often called the foreach syntax
      float f[] = new float[10];
      for(int i = 0 ; i < 10 ; i ++)
         f[i] = rand.nextFloat();
      for (float x : f) {}
      switch(integral-selector){ // requires to evaluate int or char, but can use enum
        case integral-value1 : statement;  // break is optional
        case integral-value2 : statement; break;
        default: statement;
      }

      ```
  - Method Overloading Page 120
  - Polymorphism
  -
