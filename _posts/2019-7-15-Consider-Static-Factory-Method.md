There is a nice pattern to consider while develop. And that's instead of having multiple constructors in the `class`
and creating many instances of class to use, you should then consider the static-factory-method way.

There are much advanteg using this way.

## Advantages:
 - Unlike constructors they have names. {e.g: `BigInteger(int, int, Random)` which returns a `BigInteger` that is probably prime}
   would have been better expressed as a static factory method named `BigInteger.probablePrime`
     
 - Unlike constructors, they are not required to create a new objec each time they're invoked.
   {e.g: `Boolean.valueOf(boolean)` method illustrates this technique: it never creates an object}
   This technique is similar to the Flyweight pattern [Gamma95].
 
 - Unlike constructors, they can return an object of any subtype of their return type.
   {e.g: *interface-based frameworks, where interface provide natural return types for static factory methods.}.
   `java.util.Collections` Framework API is much smaller than it would have been exported forty-five separate public
   classes, one for each convenience implementation.
   
 - The class of the returned object can vary from call to call as a function of the input parameters.
    {e.g: `EnumSet` class, has no public constructors, only static factories}
    
 - The class of the returned object not exist when the class containing the method is written.
 
 
There is a little limitations using this pattern.

## Limitations:
  - Classes without public or protected constructor cannot be subclassed.
    {e.g: It's impossible to subclass any of the convenience implementation classes in the Collections Framework}
    
  - They hard for programmer's to find. see [CommonNamingConventions.class](https://github.com/ibrahimAlii/EffectiveJavaAndKotlin/blob/master/src/Item01/java/sample2/CommonNamingConventions.java)


<iframe width="420" height="315" src="https://www.youtube.com/watch?v=gTcuG8Mr3rk"> </iframe>
