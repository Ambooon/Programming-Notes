
# Factory Function
Factory function returns an object. This means that using factory function creates a new object every time. There is no inheritance going on here, meaning that if I change the property or method in one object, it doesn't affect the other objects.

A factory function is a regular function that creates and returns a new object. It is a straightforward way to create objects and doesn’t use the `new` keyword.

#### Syntax:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.greet = function() {
    console.log(`Hello, my name is ${this.name}`);
  };
}

const person1 = new Person('Alice', 30);
person1.greet(); // Output: Hello, my name is Alice

```

#### Characteristics:

- **No `new` keyword:** You call the factory function like a regular function.
- **Flexible:** Easy to use with more control over object creation.
- **No prototype chain:** Objects created by factory functions don’t share methods via the prototype.

### Constructor Function

A constructor function is a special type of function designed to create and initialize objects. You use the `new` keyword to create instances of objects.

#### Syntax:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.greet = function() {
    console.log(`Hello, my name is ${this.name}`);
  };
}

const person1 = new Person('Alice', 30);
person1.greet(); // Output: Hello, my name is Alice

```

#### Characteristics:

- **Requires `new` keyword:** You must use `new` to create an instance.
- **Prototype chain:** Methods defined in the constructor function can be added to the prototype for shared access among all instances.

#### Example with Prototype:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.greet = function() {
  console.log(`Hello, my name is ${this.name}`);
};

const person1 = new Person('Alice', 30);
person1.greet(); // Output: Hello, my name is Alice

```

### Key Differences:

1. **Object Creation:**
    
    - **Factory Function:** Creates and returns a new object directly.
    - **Constructor Function:** Uses `new` to create and initialize an object, which is then returned implicitly.
2. **Prototype Usage:**
    
    - **Factory Function:** Objects do not share methods via prototypes unless you explicitly use `Object.create` or similar methods.
    - **Constructor Function:** Can leverage prototypes for shared methods, which can be more memory-efficient.
3. **Syntax and Usability:**
    
    - **Factory Function:** More flexible and doesn’t require the `new` keyword.
    - **Constructor Function:** Traditional way of object creation, but requires careful use of `new` to avoid errors.
4. **Inheritance:**
    
    - **Factory Function:** For inheritance, you might need to manually set up prototype chains.
    - **Constructor Function:** Inheritance can be managed more traditionally with prototype chains.

Both patterns have their uses and can be chosen based on the specific requirements of your application. For simpler cases, factory functions can be more convenient, while constructor functions (especially with prototypes) might be preferred for more complex scenarios with inheritance.

