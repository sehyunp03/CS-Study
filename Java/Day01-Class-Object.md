</> Markdown

# Day 01 - Claass and Object

## Today's Goal
Understand the difference between a class and an object.

---

## Key Concepts

### Class

A class is a blueprint for creating objects.

클래스는 객체를 만들기 위한 설계도이다.

### Object

An object is an instance of a class.

객체는 클래스를 기반으로 실제 생성된 실체이다.

### Field

A field stores the state or data of an object.

필드는 객체가 가진 정보나 상태를 저장한다.

### Method

A method defines the behavior of an object.

메서드는 객체가 할 수 있는 행동을 정의한다.

### Constructor

A constructor initializes an object when it is created.

생성자는 객체가 생성될 때 초기 상태를 설정한다.

### this

`this` refers to the current object.

`this`는 현재 객체 자기 자신을 의미한다.

---

## Class and Object Example

```java
class User {
    String name;
    int age;

    User(String name, int age) {
        this.name = name;
        this.age = age;
    }

    void login() {
        System.out.println(name + " logged in.");
    }
}
```

## What I Learned

Today I learned a Class and an Object.
They are quite different. 

A Class is a blueprint. On the other hand, an Object is instace from the Class.

## English Expressions

A class is a blueprint for creating objects.
An object is an instance of a class.
A field represents the state of an object.
A method represents the behavior of an object.
Two objects can be created from the same class.







