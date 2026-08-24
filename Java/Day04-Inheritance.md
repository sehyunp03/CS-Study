# Day 04 - Inheritance and Has-A Relationship

## 🎯 Today's Goal

Understand the difference between Inheritance (Is-A) and Composition (Has-A).

---

# 1. Inheritance

Inheritance allows a child class to inherit fields and methods from a parent class.

Example

```java
class Person {

    String name;
    int age;

}
```

```java
class Student extends Person {

    String studentId;

}
```

A Student **is a** Person.

---

# 2. Why use Inheritance?

Inheritance helps us

- reduce duplicated code
- reuse fields and methods
- express common concepts

Instead of writing the same fields in many classes, we place them in one parent class.

---

# 3. Is-A Relationship

Ask this question:

> Is A a B?

Examples

- Student is a Person ✅
- Dog is an Animal ✅
- Teacher is a Person ✅
- Bird is an Animal ✅

These are inheritance relationships.

---

# 4. Has-A Relationship

Ask this question:

> Does A have B?

Examples

- Car has an Engine ✅
- Computer has a CPU ✅
- Book has Pages ✅
- ChatRoom has Users ✅

These are composition relationships.

Example

```java
class ChatRoom {

    List<User> users;

}
```

A ChatRoom is **not** a User.

A ChatRoom **has** Users.

---

# 5. Is-A vs Has-A

| Is-A | Has-A |
|------|--------|
| Inheritance | Composition |
| Student → Person | Car → Engine |
| Dog → Animal | Computer → CPU |
| Teacher → Person | ChatRoom → User |

---

# 6. What I Learned

- Inheritance is used when an object "is a" type of another object.
- Composition is used when an object "has" another object.
- Not every relationship should use inheritance.
- Before using `extends`, I should ask, "Is A really a B?"

---

# 7. My Thoughts

Today I learned that inheritance is not just about reducing code.

The most important thing is expressing the relationship between objects.

If two objects have an "is-a" relationship, inheritance is appropriate.

If one object owns another object, composition is a better design.

---

# 8. English Expressions

- Inheritance allows code reuse.
- A Student is a Person.
- A Car has an Engine.
- Composition represents a has-a relationship.
- Think about the relationship before using `extends`.

---

# 9. Questions

- When should I use inheritance?
- When is composition a better choice?
- Why do many developers prefer composition over inheritance?
