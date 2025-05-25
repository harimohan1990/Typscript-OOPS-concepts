# Typscript-OOPS-concepts


Here’s a **TypeScript** version of OOP concepts with examples:

---

### 🔹 1. **Class and Object**

```ts
class Person {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  greet(): void {
    console.log(`Hello, I am ${this.name}`);
  }
}

const p1 = new Person("Hari");
p1.greet();
```

---

### 🔹 2. **Encapsulation (with private/protected)**

```ts
class BankAccount {
  private balance: number = 0;

  deposit(amount: number): void {
    if (amount > 0) this.balance += amount;
  }

  getBalance(): number {
    return this.balance;
  }
}

const acc = new BankAccount();
acc.deposit(1000);
console.log(acc.getBalance()); // 1000
```

---

### 🔹 3. **Inheritance**

```ts
class Animal {
  speak(): void {
    console.log("Animal speaks");
  }
}

class Dog extends Animal {
  speak(): void {
    console.log("Dog barks");
  }
}

const dog = new Dog();
dog.speak(); // Dog barks
```

---

### 🔹 4. **Polymorphism**

```ts
function makeAnimalSpeak(a: Animal) {
  a.speak();
}

const a1 = new Animal();
const d1 = new Dog();

makeAnimalSpeak(a1); // Animal speaks
makeAnimalSpeak(d1); // Dog barks
```

---

### 🔹 5. **Abstraction (via abstract class)**

```ts
abstract class Shape {
  abstract area(): number;
}

class Circle extends Shape {
  constructor(private radius: number) {
    super();
  }

  area(): number {
    return Math.PI * this.radius * this.radius;
  }
}
```

mini OOP project in TypeScript** using all key OOP principles:

---

### 📘 Project: **Online Course Management System**

---

### 🧱 **Structure & Features**

* `Course`: base class
* `LiveCourse` & `RecordedCourse`: extend `Course` (Inheritance, Polymorphism)
* `User`: encapsulates details
* Admin adds and lists courses

---

### 💻 **Code (TypeScript)**

```ts
// Abstract Class (Abstraction)
abstract class Course {
  constructor(
    public title: string,
    public instructor: string,
    protected duration: number // in hours
  ) {}

  abstract courseType(): string;

  info(): string {
    return `${this.title} by ${this.instructor}, Duration: ${this.duration} hrs`;
  }
}

// Inheritance + Polymorphism
class LiveCourse extends Course {
  constructor(title: string, instructor: string, duration: number, public time: string) {
    super(title, instructor, duration);
  }

  courseType(): string {
    return "Live";
  }
}

class RecordedCourse extends Course {
  constructor(title: string, instructor: string, duration: number, public videoCount: number) {
    super(title, instructor, duration);
  }

  courseType(): string {
    return "Recorded";
  }
}

// Encapsulation
class User {
  private enrolledCourses: Course[] = [];

  constructor(public name: string) {}

  enroll(course: Course): void {
    this.enrolledCourses.push(course);
    console.log(`${this.name} enrolled in ${course.title}`);
  }

  listCourses(): void {
    this.enrolledCourses.forEach(c =>
      console.log(`${c.title} (${c.courseType()})`)
    );
  }
}

// Usage
const course1 = new LiveCourse("React Bootcamp", "Hari", 20, "6 PM IST");
const course2 = new RecordedCourse("TypeScript Mastery", "Mohan", 15, 12);

const user = new User("John Doe");

user.enroll(course1);
user.enroll(course2);

user.listCourses();
```

---

### ✅ OOP Concepts Covered

* **Class & Object**: `Course`, `User`
* **Encapsulation**: `enrolledCourses` is private
* **Abstraction**: `Course` is abstract
* **Inheritance**: `LiveCourse`, `RecordedCourse` extend `Course`
* **Polymorphism**: `courseType()` overridden differently


