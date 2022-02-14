## Important Points

* **Field Shadowing** - When a local variable/parameter is of the same name as that of a field in class, the field is hidded and thus needs to be accessed with the `this` keywaord.

* **Covarient Return Type** - Class must return an object of the return type or an object of sub-class of the return type (or implementation if return type is of interface).

* `this` is a referece to the current object. From constructor, use the `this()` method to call other constructors of the same class.

* <table>
  <caption style="font-weight: bold" id="accesscontrol-levels">Access Levels</caption>
    <tr>
    <th id="h1">Modifier</th>
    <th id="h2">Class</th>
    <th id="h3">Package</th>
    <th id="h4">Subclass</th>
    <th id="h5">World</th>
    </tr>
    <tr>
    <td headers="h1"><code>public</code></td>
    <td headers="h2">Y</td>
    <td headers="h3">Y</td>
    <td headers="h4">Y</td>
    <td headers="h5">Y</td>
    </tr>
    <tr>
    <td headers="h1"><code>protected</code></td>
    <td headers="h2">Y</td>
    <td headers="h3">Y</td>
    <td headers="h4">Y</td>
    <td headers="h5">N</td>
    </tr>
    <tr>
    <td headers="h1" style="font-style: italic">no modifier</td>
    <td headers="h2">Y</td>
    <td headers="h3">Y</td>
    <td headers="h4">N</td>
    <td headers="h5">N</td>
    </tr>
    <tr>
    <td headers="h1"><code>private</code></td>
    <td headers="h2">Y</td>
    <td headers="h3">N</td>
    <td headers="h4">N</td>
    <td headers="h5">N</td>
    </tr>
  </table>

* Not all combinations of instance and class variables and methods are allowed:
  * Instance methods can access instance variables and instance methods directly.
  * Instance methods can access class variables and class methods directly.
  * Class methods can access class variables and class methods directly.
  * Class methods cannot access instance variables or instance methods directly—they must use an object reference. Also, class methods cannot use the this keyword as there is no instance for this to refer to.

* Instance variables can be initialized in constructors, where error handling or other logic can be used. To provide the same capability for class variables, the Java programming language includes **static initialization blocks**. 
  ```java
  static String SOME_STR; 
  static {
    SOME_STR = "here we go!";
  }
  ```

* Initializer blocks for instance variables look just like static initializer blocks, but without the static keyword.
  ```java
  String var;
  {
    var = "here it is.";
  }
  ```
  These blocks are copied into every constructor. Thus code sharing between multiple constructor can be achieved this way.

* Non-static nested classes (inner classes) have access to other members of the enclosing class, even if they are declared private. Static nested classes do not have access to other members of the enclosing class.

* To instantiate an object of Inner class, use the object of outer class like so
  ```java
  OuterClass outerObject = new OuterClass();
  OuterClass.InnerClass innerObject = outerObject.new InnerClass();
  ```
  while, static-inner classes are instantiated the same way as like other classes
  ```java
  StaticNestedClass staticNestedObject = new StaticNestedClass();
  ```

* ***Synthetic Constructs* [here](https://www.baeldung.com/java-synthetic)**

* Anonymous Claases 
  ```java
  HelloWorld frenchGreeting = new HelloWorld() {
    String name = "tout le monde";
    public void greet() {
        greetSomeone("tout le monde");
    }
    public void greetSomeone(String someone) {
        name = someone;
        System.out.println("Salut " + name);
    }
  };
  ```

* We can declare the following in anonymous classes:
  * Fields
  * Extra methods (even if they do not implement any methods of the supertype)
  * Instance initializers
  * Local classes

* We can only use lambda expressions in situations in which
the Java compiler can determine a target type - 
  * Variable declarations
  * Assignments
  * Return statements
  * Array initializers
  * Method or constructor arguments
  * Lambda expression bodies
  * Conditional expressions, `?:`
  * Cast expressions

* <table summary="Kinds of method references">
    <tr>
      <th id="h1">Kind</th>
      <th id="h2">Syntax</th>
      <th id="h3">Examples</th>
    </tr>
    
    <tr>
      <td headers="h1">Reference to a static method</td>
      <td headers="h2"><code><em>ContainingClass</em>::<em>staticMethodName</em></code></td>
      <td headers="h3"><code>Person::compareByAge</code><br/><code>MethodReferencesExamples::appendStrings</code></td>
    </tr>
    
    <tr>
      <td headers="h1">Reference to an instance method of a particular object</td>
      <td headers="h2"><code><em>containingObject</em>::<em>instanceMethodName</em></code></td>
      <td headers="h3"><code>myComparisonProvider::compareByName</code><br/><code>myApp::appendStrings2</code></td>
    </tr>
    
    <tr>
      <td headers="h1">Reference to an instance method of an arbitrary object of a particular type</td>
      <td headers="h2"><code><em>ContainingType</em>::<em>methodName</em></code></td>
      <td headers="h3"><code>String::compareToIgnoreCase</code><br/><code>String::concat</code></td>
    </tr>
    
    <tr>
      <td headers="h1">Reference to a constructor</td>
      <td headers="h2"><code><em>ClassName</em>::new</code></td>
      <td headers="h3"><code>HashSet::new</code></td>
    </tr>
    
  </table>