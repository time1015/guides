# Conventions and Practices for Java

## Disclaimer

This highly documents the various ways I write code in Java, and only reflects my own set of preferences in writing such code. I am not imposing this set of conventions to other people, but I may impose this to some of my other personal projects. Nevertheless, I hope this gives you an idea on what to adapt or take into your own.

## Conventions

### Formatting
* Implement 2-space indentation.
* List `@` annotations on a per-line basis.
* When listing at least 2 elements of an array, list the elements on a per-line basis.
* When doing method chaining, list the method calls (except for the call that starts the chain) on a per-line basis.
* Generally, member order go as follows:
  1. Non-final static members (Public, then private)
  2. Final static members (Public, then private)
  3. Static methods (Public, then private)
  4. Non-final instance members (Public, then private)
  5. Final instance members (Public, then private)
  6. Instance methods (Public, then private)
  7. `static {}` block
* In some cases, the member order may not be followed in favor of readability. This order only mandates a minimum standard for consistency. Nevertheless, this order should be implemented by default.

### Imports
* Remove unused imports.
* Swap wildcard imports (`import some.package.*`) with imports to specific classes referenced from that wildcard import.
* List imports in alphabetical order, with static imports (`import static`) on top.
* Maintain readability when using static imports.

### Unit Tests
* Write unit tests for the following:
  * Concrete classes
  * Default methods of interfaces
  * Non-abstract methods of abstract classes
  * Static methods of classes and interfaces
* Maintain consistency of unit test imports:
  * Statically import the `org.junit.jupiter.api.Assertions` class.
  * If mocking is needed:
    * Statically import the `org.mockito.Mockito` class and its related classes.
    * Use a `static {}` block to initialize mocking of classes. This is to offload classloading times from test case executions.
* Arrange the unit tests in the same order as the methods under test.

## Practices

### Names
* Write specific and descriptive names.
  * Avoid using vague names like `temp`, `obj`, and one-letter variable names (except in loops).
  * Avoid using suffixes like `Manager`, `Object`, `Entity`, `Controller`, etc.
* Getters and setters must not be prefixed with `get` and `set` respectively.
  * A noun for a method name often denotes a member inside a class, and usually means that it's a getter, a setter, or both:

```
public String name() {
  return name;
}

public void name(String name) {
  this.name = name;
}
```

* Prefix member access inside classes with `this`.

### Variables and Constants
* Avoid reusing variables for other purposes.
  * Declare variables only within the exact context they're being used.
* Avoid using too many variables.
  * This could be a sign of a [potentially long method](https://refactoring.guru/smells/long-method) since the presence of many variables may entail presence of many contexts that could have been [extracted into smaller, more readable code](https://refactoring.guru/extract-method).
* Avoid committing the mistake of [Primitive Obsession](https://refactoring.guru/smells/primitive-obsession).

### Writing Code
* Keep methods and classes short and descriptive.
* Write methods and classes that serve only one purpose, and operate within a single context.
* Avoid [long methods](https://refactoring.guru/smells/long-method) and [unnecessarily large classes](https://refactoring.guru/smells/large-class).
  * Refactor them into smaller, isolated components.
* Avoid duplicate code.
  * Refactor them into classes or methods as necessary.
* Avoid comments.
  * Likewise, avoid commented code.
* Avoid [too many parameters](https://refactoring.guru/smells/long-parameter-list) in methods.

### Designing
* Avoid [Speculative Generality](https://refactoring.guru/smells/speculative-generality).
* Follow the [SOLID Principles of Object-Oriented Design](https://scotch.io/bar-talk/s-o-l-i-d-the-first-five-principles-of-object-oriented-design) as necessary.
* Make use of [Design Patterns](https://refactoring.guru/design-patterns) as necessary.

## Sources
* [Refactoring.guru](https://refactoring.guru/) - a good site that documents Refactoring, Code Smells, and Design Patterns
* [SOLID Principles of Object-Oriented Design](https://scotch.io/bar-talk/s-o-l-i-d-the-first-five-principles-of-object-oriented-design) - an article that explains and demonstrates the SOLID Principles by Samuel Oloruntoba
