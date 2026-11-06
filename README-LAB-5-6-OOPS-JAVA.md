# LAB 5 & 6 – OOPS with Java


**Topic:** Packages and Exception Handling  
**Name:** Punith C  
**USN:** 1BF25CS196  
**College:** BMS College of Engineering

## Overview

This lab record contains three Java programs demonstrating user-defined packages and exception handling:

1. **TransactionProject** – Uses user-defined packages (`transaction` and `reports`) and import statements.
2. **Rails.java** – Railway seat reservation using a custom exception, `throw`, `throws`, multiple `catch` blocks, and `finally`.
3. **Divide.java** – Handles division by zero using `try-catch`.

---

## 1. TransactionProject – User-Defined Packages

### Aim

To create a bank-account program in which classes are placed in two packages (`transaction` and `reports`) and used from a main class with import statements.

### Project structure

```text
TransactionProject/
├── transaction/
│   └── Account.java
├── reports/
│   └── TransactionReport.java
└── MainApplication.java
```

### Files

- `transaction/Account.java` – Stores the account number and balance; provides deposit, withdraw, and getter methods.
- `reports/TransactionReport.java` – Imports `transaction.Account` and generates an account report.
- `MainApplication.java` – Imports both classes, creates an account, performs transactions, and displays the report.

### Compile and run

Run these commands from inside the `TransactionProject` directory:

```bash
javac -d . transaction/Account.java reports/TransactionReport.java MainApplication.java
java MainApplication
```

### Expected output

```text
Initial Balance: 5000.0
Amount Deposited: 2000.0
Amount Withdrawn: 1000.0

--- Transaction Report ---
Account Number: 101
Current Balance: 6000.0
```

### Concepts demonstrated

- Packages organise related Java classes.
- `import` allows a class to use a class from another package.
- Private data is accessed through getter methods.
- Deposit and withdrawal operations validate the amount and balance.

---

## 2. Rails.java – Railway Seat Reservation

### Aim

To reserve seats in a train with five seats, using a user-defined exception for an already booked seat and handling incorrect inputs with `try`, `catch`, and `finally`.

### Compile and run

```bash
javac Rails.java
java Rails
```

### How it works

- The reservation system contains five seats.
- `SeatAlreadyBookedException` is a custom exception that extends `Exception`.
- `reserveSeat(int seat)` checks whether the seat number is between 1 and 5.
- An invalid seat number causes an `IllegalArgumentException`.
- Selecting an already booked seat causes a `SeatAlreadyBookedException`.
- `InputMismatchException` handles non-numeric input such as `abc`.
- The `finally` block prints the completion message and closes the `Scanner`.

### Sample test inputs

Enter the following inputs when prompted:

```text
2
2
8
abc
1
```

### Expected behaviour

| Input | Expected message | Reason |
|---|---|---|
| `2` | `Seat reserved successfully!` | Seat 2 is available. |
| `2` again | `Seat already booked!` | Seat 2 has already been reserved. |
| `8` | `Invalid seat number!` | Valid seat numbers are 1 to 5. |
| `abc` | `Incorrect input! Enter numbers only.` | The input is not an integer. |
| `1` | `Seat reserved successfully!` | Seat 1 is available. |

At the end, the `finally` block prints:

```text
Transaction completed.
```

---

## 3. Divide.java – Handling ArithmeticException

### Aim

To divide two numbers entered by the user and handle division by zero without the program crashing.

### Compile and run

```bash
javac Divide.java
java Divide
```

### How it works

- A `Scanner` reads two integers.
- The division operation is performed inside a `try` block.
- Dividing an integer by zero causes an `ArithmeticException`.
- The `catch` block handles the exception and prints an error message.

### Sample run 1

```text
Enter first number: 10
Enter second number: 5
Result: 2
```

### Sample run 2

```text
Enter first number: 10
Enter second number: 0
Cannot divide by zero!
```

---

## Verification and observations

The programs and outputs were checked as recorded in the lab document.

| Program | Test | Result |
|---|---|---|
| TransactionProject | Initial balance 5000, deposit 2000, withdraw 1000 | Correct; final balance 6000 |
| Rails.java | Reserve seat 2 | Correct |
| Rails.java | Reserve seat 2 again | Correct custom exception |
| Rails.java | Enter seat 8 | Correct invalid-seat message |
| Rails.java | Enter `abc` | Correct input-error message |
| Divide.java | Divide 10 by 5 | Correct; result 2 |
| Divide.java | Divide 10 by 0 | Correct division-by-zero message |

### Notes

- The lab record notes that `Divide.java` has a Scanner resource warning because the Scanner is not closed. Adding `sc.close()` after input processing can remove the warning.
- In the recorded version of `Divide.java`, the two `nextInt()` calls are outside the `try` block. Non-numeric input such as `abc` is therefore not handled by that program.
- `Rails.java` uses five loop iterations, meaning five reservation attempts, not necessarily five successful bookings.

---

## Conclusion

- Packages organise classes into separate folders, and `import` allows classes from other packages to be used.
- `try`, `catch`, and `finally` help handle runtime errors.
- Custom exceptions allow programs to report application-specific errors, such as an already booked railway seat.
- `ArithmeticException` can be handled to prevent division-by-zero errors from terminating a program unexpectedly.

---

**Lab:** 5 & 6 – OOPS with Java  
**Student:** Punith C  
**USN:** 1BF25CS196  
**Institution:** BMS College of Engineering
