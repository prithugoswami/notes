# Chapter 9 -- Packages & Interfaces

## Packages
- It is a mechanism provided by java to manage namespaces.
- It is both a naming and visibility control mechanism.
- Java uses filesystem directories to store packages. Therefore declaring a 
package as:

    ```
    package MyPackage;
    ```
  should also reflect in the filesystem with the **same name and case**
- Another example:

    ```
    package org.prithu.image;
    ```
    needs to be stored in `org/prithu/image`


## Finding Packages and `CLASSPATH`
- By default, java runtime system uses the current working directory as its
starting point to search for packages
- Second, `CLASSPATH` environmental variable can point to directories
- Third, using `-classpath` option with `java` and `javac`

I order for a program to find **`MyPack`** one of the things must be true:

1. Program is executed in a directory immediately above **`MyPack`**
2. `CLASSPATH` must be set to include the path to **`MyPack`**
3. `-classpath` option must specify the path to **`MyPack`**

while using 2. and 3. the *path to* **`MyPack`** must be specified and not
**`MyPack`** itself.\

## Access Protection
- Classes and packages are both means of encapsulating and containing the 
namespace and scope of variable and methods. Packages act as containers for
classes and other subordinate packages.


: Class Member Access

+-------------------+---------+-------------+-----------+---------+
|                   | Private | No Modifier | Protected | Public  |
+===================+=========+=============+===========+=========+
| Same class \      | **Yes** | **Yes**     | **Yes**   | **Yes** |
|                   |         |             |           |         |
+-------------------+---------+-------------+-----------+---------+
| Same package\     | No      | **Yes**     | **Yes**   | **Yes** |
| subclass          |         |             |           |         |
|                   |         |             |           |         |
+-------------------+---------+-------------+-----------+---------+
| Same package\     | No      | **Yes**     | **Yes**   | **Yes** |
| non-subclass      |         |             |           |         |
|                   |         |             |           |         |
+-------------------+---------+-------------+-----------+---------+
| Different package\| No      | No          | **Yes**   | **Yes** |
| subclass          |         |             |           |         |
|                   |         |             |           |         |
+-------------------+---------+-------------+-----------+---------+
| Different package\| No      | No          | No        | **Yes** |
| non-subclass      |         |             |           |         |
|                   |         |             |           |         |
+-------------------+---------+-------------+-----------+---------+

- When a class is declared `public` it must be the only class declared in the
file
- If a class is `public` it can be accessed by any code but if it has
default
access, then it can only be accessed only from within its same package

## Importing Packages
- The import statement brings certain classes, or entire packages, into
visibility and then a class can be referred directly by name. (instead of using
the fully-qualified name)
- `import` statements occur immediately following the package statement
  ```
  import pkg[.pkg2].(classname | *);
  ```
- The star form may increase **compilation time**---especially if you
import
several large packages. It's a good practice to only import the classes
you
need. Although the star form has no effect on run-time performance.
- The `java.lang` package is automatically imported during compilation
- When a package is imported (using `*`) only **public** classes will be
available to **non-subclasses** in the importing code
- `import` is a convenience, but, any where a class name is used, you can use
it's *fully qualified name*.

**With `import`**
```
import java.util.*;
class MyDate extends Date{
}
```
**Without `import`**
```
class Mydate extends java.util.Date{
}
```

## Interfaces
- Complete abstraction possible using Interfaces. Specifies what a
class must do, but not how it does it.
- Similar to classes but they lack instance variables, and the methods have
not body
- A class that implements the interface must define all the methods from the
interface.
- They disconnect the definition of the method from the class hierarchy, ie.
A class must not depend on inheritance to gain some functionality.
- Here it is possible for classes to implement an interface that is unrelated
to it's class hierarchy. Thus it avoids the problem where more functionality
is added to the superclass.
- variables declared inside must be initialized and are implicitly declared
`final` and `static`
- If a class implements two interfaces that declare the same method, then 
the same method will be used by clients of either interface.
- The methods that implement an interface must be declared **public**
- A variable to reference objects implementing an interface can be made using
the name of the interface. When a method is called using this reference
variable, the version of the method called depends on the object being
referred to just like DMD.
- Although, the Interface type variable knows only about it's methods and
cannot access any other member of the implementing class
- A class partially implementing an Interface must be declared abstract.

*Dynamic lookup of a method is a significant overhead
when compared to normal method invocation, you should
be careful not to use interfaces casually in 
performance-critical systems*

### Example:

```
interface Callback {
    void callback(int param);
}

class Client implements Callback {
    public void callback(int p){
        System.out.println("Client: callback called with" + p);
    }


class AnotherClient implements Callback {
    public void callback(int p) {
        System.out.println("AnotherClient: p squared" + (p*p));
    }
}
```
