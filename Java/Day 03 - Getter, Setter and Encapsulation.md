# Day 03 - Getter, Setter and Encapsulation

## 🎯 Today's Goal

Understand why Getter and Setter exist and learn the concept of Encapsulation.

---

# 1. Getter

A Getter is a method that returns the value of a private field.

Example

```java
public String getName() {
    return name;
}
```

Getter allows other classes to read data safely.

---

# 2. Setter

A Setter is a method that changes the value of a private field.

Example

```java
public void setName(String name) {
    this.name = name;
}
```

A Setter can validate data before changing it.

Example

```java
public void setAge(int age) {

    if(age < 0){
        return;
    }

    this.age = age;
}
```

---

# 3. Encapsulation

Encapsulation means protecting data and allowing access only through methods.

Instead of

```java
user.password = "1234";
```

we use

```java
user.changePassword("1234");
```

Advantages

- Protect important data
- Validate user input
- Easy to extend new features
- Prevent invalid values

---

# 4. Why don't we make every field public?

If every field is public,

```java
user.age = -100;
```

is possible.

Using private prevents invalid data.

---

# 5. Do all fields need Getter and Setter?

No.

Example

| Field | Getter | Setter |
|--------|:------:|:------:|
| name | ✅ | ✅ |
| age | ✅ | ⭕ Depends |
| studentId | ✅ | ❌ |
| gpa | ✅ | ❌ |
| password | ❌ | ❌ |

Not every field needs both methods.

---

# 6. Store or Calculate?

One important design question is:

> Should we store this data, or calculate it when needed?

Example

Instead of

```java
private int age;
```

store

```java
private LocalDate birthDate;
```

Age can always be calculated from the birth date.

This prevents inconsistent data and keeps the original information.

---

# 7. What I Learned

- Getter is used to read private data.
- Setter is used to modify private data safely.
- Encapsulation protects important information.
- Not every field needs Getter and Setter.
- Sometimes it is better to calculate data than store it.

---

# 8. My Thoughts

At first, I thought every piece of information should be stored.

However, I learned that some values can be calculated whenever they are needed.

For example, storing a birth date is better than storing age because age changes every year.

A good programmer should think about whether data should be stored or calculated.

---

# 9. English Expressions

- A getter returns the value of a field.
- A setter updates the value of a field.
- Encapsulation protects data.
- Some values should be calculated instead of stored.
- Store original data whenever possible.

---

# 10. Questions

- When should we store data?
- When should we calculate data?
- Why doesn't every field have a Setter?
