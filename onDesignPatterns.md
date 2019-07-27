


# Design Patterns

## When to use the Singleton pattern

- Very few 'good' reasons to use Singleton
- Classic example is the good ole logger
- Logging is a specific example of an "acceptable" Singleton because it doesn't affect the execution of your code. 
- Disable logging, code execution remains the same. Enable it, same same.
- You could possibly argue that configuration files could use Singletons but what if configuration is moved to the db...

## When to consider using the Builder pattern

> "The builder pattern is a good choice when designing classes whose constructors or static factories would have more than a handful of parameters." - Joshua Bloch 
- This pattern is flexible and it is easy to add more parameters to it in the future. 
- It is really only useful if you are going to have more than 4 or 5 parameters for a constructor. 
- It might be worthwhile in the first place if you suspect you may be adding more parameters in the future.
- For 'natural' looking code
- Pizza pizza = new Pizza.Builder(10).cheese(true).peperoni(true).bacon(true).build();
- When you want to guarantee that your object can't be constructed in an inconsistent state 
- You have too many fields to set using constructor parameters would make it difficult to use and read

## When to consider using the Factory pattern

- When the factory can easily create the entire object within one method call.


