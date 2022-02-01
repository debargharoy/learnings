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

*  Non-static nested classes (inner classes) have access to other members of the enclosing class, even if they are declared private. Static nested classes do not have access to other members of the enclosing class.