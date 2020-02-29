## Java 8 Features (Java Lambda Expressions and Functional interfaces)
### Java Lambda Expressions
Is one of the best feature in Java 8. I really like it because it is the first step to Functional Programming.

See an example with one argument
```
Object object = str -> System.out.println("Hi"+ str);
```

Another, simple example without argument
```
Object object = () -> System.out.println("Hi Dear");
```

Another one, with two statements in the method and two arguments
```
Object object = (str1, str2) -> {
	String str = "First string = " + str1 + " and the second one = " + str2;
	System.out.println(str);
}
```

### Functional interfaces
Functional interfaces are defined as interfaces that are only one abstract method. The anotation used here is @FunctionalInterface.

This is an example for a simple Functional interface
```
@FunctionalInterface
public interface SampleFunctionalInterface {

    abstract String abstFunctionIntermethod(String str);
}
```

Now, I want to combine the lambda expression with functional interface. Let's see this simple example:
```
import com.adipster.SampleFunctionalInterface;

public class Main {

	public static void main(String[] args) {

		SampleFunctionalInterface lambdaEx = str -> System.out.println("Hi"+ str);

		lambdaEx.abstFunctionIntermethod("Emile");// Output : Hi Emile
	}
}
```

An important functional interface here is Consumer<T> interface. 
The Consumer<T> interface in java.util.function package takes up a single argument of any given type and provides a void method that consumes the provided argument.
```
@FunctionalInterface
public interface Consumer<T> {
    void accept(T var1);
}
```

Now, we are using Consumer interface to implement the previous example.
```
import java.util.function.Consumer;

public class Main {

	public static void main(String[] args) {

		Consumer<String> lambdaEx = str -> System.out.println("Hi"+ str);

		lambdaEx.accept("Emile");// Output : Hi Emile
	}
}
```

Another good interface is Function<T,R> interface in  java.util.function. 
```
@FunctionalInterface
public interface Function<T, R> {
    R apply(T var1);
}
```

With the previous interface, we can write a lambda expression that takes up one argument of any type and returns a value of any type.
Let's see the result with our previous example.
```
import java.util.function.Function;

public class Main {

	public static void main(String[] args) {

		Function<String, Integer> lambdaEx = str -> str.length();

		System.out.println(lambdaEx.apply("Emile"));// Output : 5
	}
}
```
## Reference
[1] https://www.oracle.com/webfolder/technetwork/tutorials/obe/java/Lambda-QuickStart/index.html
