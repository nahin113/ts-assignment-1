Access Modifiers in TypeScript OOP
Introduction
Access modifiers in Object-Oriented Programming (OOP) are keywords used to control the visibility and security of class properties and methods. They are essential in TypeScript because they help enforce data encapsulation and protect internal state during compile-time checks.

Public, Private, Protected, and Readonly
TypeScript provides four primary access modifiers: public, private, protected, and readonly. public members can be accessed from anywhere, whereas private members are restricted strictly to their containing class. protected members allow access within the class and its subclasses, while readonly ensures that a property cannot be modified after initial assignment.

TypeScript
class Employee {
  public name: string;
  private baseSalary: number;
  protected department: string;

  constructor(name: string, baseSalary: number, department: string) {
    this.name = name;
    this.baseSalary = baseSalary;
    this.department = department;
  }
}
Practical Implementation with Inheritance
The example below demonstrates how these modifiers operate across a superclass and a subclass. While protected properties remain accessible to derived classes, private members stay safely hidden.

TypeScript
class Person {
  public name: string;
  protected role: string;
  private idNumber: number;

  constructor(name: string, role: string, idNumber: number) {
    this.name = name;
    this.role = role;
    this.idNumber = idNumber;
  }

  public getPublicInfo(): string {
    return `Name: ${this.name}, Role: ${this.role}`;
  }
}

class EmployeeRecord extends Person {
  readonly organization: string;

  constructor(name: string, role: string, idNumber: number, organization: string) {
    super(name, role, idNumber);
    this.organization = organization;
  }

  public getDepartmentDetails(): string {
    return `Employee ${this.name} works as a ${this.role} at ${this.organization}.`;
  }
}

const emp = new EmployeeRecord("Alice", "Developer", 101, "TechCorp");
console.log(emp.getDepartmentDetails());
Conclusion
In summary, utilizing access modifiers dramatically increases code security, predictability, and maintainability in object-oriented applications. Proper encapsulation prevents unauthorized state mutations and keeps large-scale TypeScript architectures clean and robust.
