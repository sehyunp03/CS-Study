# Day 05 - Polymorphism

## 🎯 Today's Goal

Understand why polymorphism is needed and how a parent reference can manage different child objects.

---

# 1. What is Polymorphism?

Polymorphism means "one interface, many forms."

A parent reference can point to different child objects.

Example

```java
Animal animal = new Dog();
```

The variable type is `Animal`, but the actual object is `Dog`.

---

# 2. Upcasting

Upcasting means using a child object as a parent type.

Example

```java
Animal animal = new Dog();
```

Why?

Because **Dog is an Animal**.

Upcasting allows us to manage different child objects with one parent type.

---

# 3. Method Overriding

A child class can redefine a method inherited from the parent class.

Example

```java
class Animal {

    void sound() {
        System.out.println("Animal");
    }

}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Dog");
    }

}
```

Example

```java
Animal animal = new Dog();
animal.sound();
```

Output

```text
Dog
```

The overridden method in the actual object (`Dog`) is executed.

---

# 4. Why do we use a parent reference?

Without polymorphism

```java
Dog dog = new Dog();
Cat cat = new Cat();
Bird bird = new Bird();
```

Every object needs its own variable.

With polymorphism

```java
List<Animal> animals = new ArrayList<>();

animals.add(new Dog());
animals.add(new Cat());
animals.add(new Bird());
```

Now all animals can be managed together.

---

# 5. Is-A Relationship

Ask this question before using inheritance.

> Is A a B?

Examples

✅ Dog is an Animal.

✅ Teacher is a Person.

❌ Car is an Engine.

---

# 6. Upcasting Rules

| Code | Possible? | Reason |
|------|:---------:|--------|
| `Animal animal = new Dog();` | ✅ | Dog is an Animal. |
| `Dog dog = new Animal();` | ❌ | Not every Animal is a Dog. |
| `Person person = new Teacher();` | ✅ | Teacher is a Person. |
| `Teacher teacher = new Person();` | ❌ | Not every Person is a Teacher. |

---

# 7. What I Learned

- Polymorphism allows different child objects to be treated as one parent type.
- Java executes the overridden method of the actual object.
- Upcasting is possible because a child object is also a parent object.
- Polymorphism makes object management easier.

---

# 8. My Thoughts

At first, I thought polymorphism was only about overriding methods.

However, I learned that its real purpose is to manage many different objects in the same way.

Using a parent reference makes the program easier to extend and maintain.

---

# 9. English Expressions

- Polymorphism allows one interface to have many implementations.
- A parent reference can refer to a child object.
- Method overriding changes inherited behavior.
- Upcasting allows code reuse.
- A Dog is an Animal.

---

# 10. Questions

- When should I use polymorphism?
- Why can't a parent object become a child object?
- How does Java know which overridden method to execute?
