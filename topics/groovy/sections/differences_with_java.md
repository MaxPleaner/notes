**Differences with Java**

_Auto-imported packages_

- java.io.*
- java.lang.*
- java.math.BigDecimal
- java.math.BigInteger
- java.net.*
- java.util.*
- groovy.lang.*
- groovy.util.*

_Runtime dispatch_

When the program is compiled, methods are delegated based on types. In Java, this happens in compile-time, but it happens at runtime in Groovy.

_Array literals_

Groovy requires `[1,2,3]` not `{1,2,3}`

_Getter/Setter_

```java
  class Person {
    String name
  }
```

This will create a `name` getter/setter instead of a "package-private field".

Use `@PackageScope String name` to get the private field. 

_ARM blocks_

"Automatic resource management" is rewritten in groovy to be more concise. 

_Nested static class_

```groovy
class A {
    static class B {}
}
new A.B()
```

_Nested anonymous class_

Groovy uses `new X(y)` instead of `y.new X()`

```groovy
public class Y {
    public class X {}
    public X foo() {
        return new X()
    }
    public static X createX(Y y) {
        return new X(y)
    }
}
```

_Lambdas_

```groovy
Runnable run = { println 'run' }
list.each { println it } // or list.each(this.&println)
```

_String class_

`GString` is the class for strings which contain `${}` interpolation (instead of `String`).

_Casting to char_

`(char) stringVal` will raise error for multi-char strings

`stringVal as char` will select the first character for multi-char strings

_Equality tester_

In Java, `==` means equality of primitive types or identity for objects.

In Groovy, `==` translates to `a.compareTo(b)` if they are `Comparable`, and `a.equals(b)` otherwise. To check for identity, there is `a.is(b)`

_Type conversion_

See [examples/type_conversion.chart.md](examples/type_conversion.chart.md)

_Extra keywords_

`as`

`def`

`in`

`trait`