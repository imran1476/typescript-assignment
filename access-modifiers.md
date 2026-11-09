# Access Modifiers in TypeScript OOP

## Introduction
Access modifiers control who can read or change the members of a class. They help us hide internal details and protect data. TypeScript provides `public`, `private`, `protected`, and `readonly`.

## Body
By default, every member is `public`, so it can be accessed from anywhere. A `private` member is available only inside its own class. A `protected` member is also available in subclasses, but not outside. The `readonly` modifier allows a property to be assigned only once, in its declaration or in the constructor.

```ts
class Account {
  public owner: string;
  private balance: number;
  protected bankName: string;
  readonly id: number;

  constructor(owner: string, balance: number, id: number) {
    this.owner = owner;
    this.balance = balance;
    this.bankName = "Demo Bank";
    this.id = id;
  }

  getBalance(): number {
    return this.balance;
  }
}

class SavingsAccount extends Account {
  getBank(): string {
    return this.bankName;
  }
}

const account = new Account("Rakib", 500, 1);
// account.balance = 0;  // Error: private
// account.id = 2;       // Error: readonly
```

Here, `SavingsAccount` can read `bankName`, but code outside the class cannot. Note that these checks happen at compile time only.
These modifiers are useful when designing real-world applications with multiple classes. For example, a banking application can keep account balances private while providing a public method to retrieve the balance safely. A protected property can be shared with specialized subclasses without exposing it to unrelated code. Choosing the correct modifier improves security at the code design level and makes maintenance easier.

## Conclusion
Access modifiers enforce encapsulation and make classes safer and easier to maintain. Use `private` by default and open access only when needed.
