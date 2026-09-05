# Day 06 - Designing the User Class

## 🎯 Today's Goal

Start designing a Java chat application and apply the OOP concepts learned from Day 1–5.

Today I focused on designing the `User` class and deciding which data and responsibilities should belong to it.

---

## 1. Chat Application Objects

A simple chat application may contain objects such as:

- User
- ChatRoom
- Message

For example:

```text
ChatRoom has Users.
```

This is a **Has-A relationship**.

Later, multiple users can be managed using a `List`.

```java
List<User> users = new ArrayList<>();
```

---

## 2. Designing User Fields

I considered the following fields:

```java
private String id;
private String password;
private String nickname;
private LocalDate birthDate;
private LocalDateTime lastLoginTime;
```

### Why store these values?

| Field | Store? | Reason |
|---|---|---|
| `id` | Yes | Needed to identify/login a user |
| `password` | Yes | Needed for authentication |
| `nickname` | Yes | Used as the user's displayed name |
| `age` | No | Can be calculated from `birthDate` |
| `birthDate` | Yes | Source data used to calculate age |
| `online` | No | Can later be determined from session/socket state |
| `lastLoginTime` | Yes | Records the user's last login time |

### Important Idea

Not every value needs to be stored.

If a value can be calculated from reliable source data, it may be better to calculate it when needed.

For example:

```text
birthDate → store
age → calculate
```

---

## 3. Private Fields and Constructor

A `private` field can still be accessed inside the same class.

Therefore, the constructor can initialize private fields.

```java
User(String id, String password, String nickname, LocalDate birthDate) {
    this.id = id;
    this.password = password;
    this.nickname = nickname;
    this.birthDate = birthDate;
}
```

`private` means that code outside the class cannot directly access the field.

---

## 4. Getter and Modification Methods

### ID

```java
public String getId() {
    return id;
}
```

The ID can be read, but normally should not be freely changed after account creation.

Therefore, a public `setId()` is not necessary.

### Nickname

```java
public String getNickname() {
    return nickname;
}
```

The nickname can be changed through a method such as:

```java
public void changeNickname(String nickname) {
    this.nickname = nickname;
}
```

### Password

A password should not have a normal Getter.

Instead of:

```java
getPassword()
setPassword()
```

it is better to provide behavior such as:

```java
changePassword(...)
```

This allows validation rules to be added.

---

## 5. Calculating Age

Instead of storing `age`, I store `birthDate`.

```java
private LocalDate birthDate;
```

The current age can then be calculated when needed.

```java
public int getAge() {
    LocalDate now = LocalDate.now();
    Period age = Period.between(birthDate, now);

    return age.getYears();
}
```

Required imports:

```java
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.Period;
```

### Important

The order of `Period.between()` matters.

```java
Period.between(birthDate, now);
```

means:

```text
birth date → current date
```

---

## 6. Responsibility of a Class

One of today's most important ideas was deciding:

> Who should be responsible for this behavior?

At first, a User seems to perform actions such as:

```text
login
logout
sendMessage
joinRoom
changeNickname
changePassword
```

However, the person performing an action does not necessarily mean that the `User` class should implement all of it.

For example:

```text
User
→ manages its own information

AuthService
→ authentication/login

ChatRoom
→ manages users in a room

ChatService
→ message-related operations
```

The exact design may change as the project develops.

---

## 7. Nickname Validation

A User can validate information about its own nickname.

For example:

```text
Is the nickname empty?
Is it too long?
Is it valid?
```

However, checking whether another user already has the same nickname requires information about other users.

Therefore, another object such as a `UserManager` can be responsible for checking duplication.

```text
UserManager
    ↓
Check whether nickname already exists
    ↓
If available
    ↓
User changes nickname
```

### Key Idea

A class should usually be responsible for information that it knows and manages.

---

## 8. Password Validation

Instead of blindly changing a password:

```java
this.password = newPassword;
```

the program should validate it first.

For example:

```java
public boolean changePassword(String newPassword) {

    if (newPassword == null || newPassword.length() < 8) {
        return false;
    }

    this.password = newPassword;
    return true;
}
```

The `User` class determines whether the value is valid.

The UI can decide what to do when the change fails.

```text
User
→ validate password
→ return success/failure

UI
→ receive failure
→ ask the user to enter another password
```

This is an example of **separation of responsibilities**.

> Note: A real application should not store passwords as plain text. This project currently simplifies password handling for OOP practice.

---

## 9. Current User Class

The current design is approximately:

```java
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.Period;

class User {

    private String id;
    private String password;
    private String nickname;
    private LocalDate birthDate;
    private LocalDateTime lastLoginTime;

    User(String id, String password, String nickname, LocalDate birthDate) {
        this.id = id;
        this.password = password;
        this.nickname = nickname;
        this.birthDate = birthDate;
    }

    public String getId() {
        return id;
    }

    public String getNickname() {
        return nickname;
    }

    public int getAge() {
        LocalDate now = LocalDate.now();
        Period age = Period.between(birthDate, now);

        return age.getYears();
    }

    public void changeNickname(String nickname) {
        this.nickname = nickname;
    }

    public void changePassword(String password) {
        this.password = password;
    }
}
```

This is not the final version.

Validation and other responsibilities will be improved as the project develops.

---

## 10. What I Learned

- Private fields can be initialized through a constructor.
- `LocalDate` can represent a date.
- Age does not need to be stored if it can be calculated from `birthDate`.
- A method's return type should match the value it actually returns.
- `void` is used when a method does not return a value.
- Validation should happen before changing important data.
- Not every action performed by a user should belong to the `User` class.
- Class responsibilities should be separated based on which object owns or knows the necessary information.

---

## 11. English Practice

My sentence:

> The User class manages the user information and information that user can directly change in chatting app.

More natural version:

> The User class manages user information and data that the user can directly modify in a chat application.

Useful expressions:

- manage user information
- modify user data
- validate input
- store data
- calculate age
- separation of responsibilities
- The User class represents a user in the chat application.

---

## 12. Next Step

Next, I will continue implementing the chat application and learn new Java concepts when they become necessary.

Possible next topics:

- Input validation
- `List` and `ArrayList`
- User management
- ChatRoom
- Exceptions
- Networking and sockets
