---
geometry:
- lmargin=0.9in
- rmargin=0.5in
- tmargin=0.3in
- bmargin=0.5in
- twoside
papersize: a4
classoption:
...

## Understanding Static
- When a member is declared static, it can be accessed before any objects of
its class are created, and without reference to any abject.
- They are essentially global variables.
- When objects of it's class are declared, no copy of the static variable is
made. Instead, **all instances of the class share the same static variable**.
- It's a way to used global variables and methods. One example could be 
a static variable to store the API key for an application that consumes some
REST API
- Methods declared as static have restrictions on them:
  * They can only call other static methods (memebers of the same class).
  * They must only access static data (members of the same class).
  * They cannot refer to `this` or `super` in any way.
- If computation is required in order to initialize static variables, it can
be done in a `static` block. This block gets executed exactly once, when the
class is first loaded
```
//demonstrate static variables, methods and blocks.
class UseStatic {
    static int a = 3;
    static int b;

    static void meth(int x){
        System.out.println("x = " + x);
        System.out.println("a = " + a);
        System.out.println("b = " + b);
    }

    static {
        System.out.println("Static block");
        b = a * 4;
    }

    public staic void main(String args[]) {
        meth(42);
    }
}
```
- As soon as UseStatic is loaded, all the static statements are run.

Output:

```
Static block
x = 42
a = 3
b = 12
```
- Outside of the class in which they are define, static methods and variables
can be used by use of the *dot operator*
- Eg: *`ClassName.mehtod`*`()`, *`ClassName.variable`*`()`

## Introducing Nested & Inner Classes
- A nested class has acces to the members, including *private* members, of the
class in which it is nested.
- The enclosing class does not have access to the members of the nested class
- **2 Types of nested classes**
  * *Static* - It cannot refer to members of the enclosing class directly. It
  must access the members of the enclosing class through an
  object, as it is `static`
  * *Non-Static* - An inner class is a non-static nested class. It can refer
  to the members of the outer class directly just like how other non-static
  members do.

&nbsp;

&nbsp;

### Example: Demonstrate an inner class

```
class Outer {
    int outer_x = 100;
    
    void test() {
        Inner inner = new Inner();
        inner.display();
    }

    class Inner {
        void display() {
            System.out.println("display: outer_x = " + outer_x);
        }
    }
}

class InnerClassDemeo {
    public static void main(String args[]) {
        Outer outer = new Outer();
        outer.test();
        // main -> Outer.test -> Inner.display -> outer_x(direct access)
    }
}
```

*Output:*
```
display: outer_x = 100
```
&nbsp;

- Instance of `Inner` can only by created within the scope of `Outer`
- However to create an instance of `Inner` outside of the scope of `Outer`,
full name can be qualified with `Outer.Inner`.
- Members of the inner class are known only to the inner class and cannot be
used by the outer class
- *Also, It is possible to define an inner class within any block scope*

### Example: Define an inner class within a for loop
```
class Outer {
    int outer_x = 100;
    
    void test() {
        for(int i=0; i<5; i++) {
            class Inner{
                void display() {
                    System.out.println("Display: outer_x = " + outer_x);
                }
            }
            Inner inner = new Inner ();
            inner.display();
        }
    }
}

class InnerClassDemo {
    public static void main(String args[]) {
        Outer outer = new Outer();
        outer.test();
    }
}


```
*Output:*
```
display: outer_x = 100
display: outer_x = 100
display: outer_x = 100
display: outer_x = 100
display: outer_x = 100
```
