# Enhanced Cash Register

This project involves enhancing the `CashRegister` class by creating an `ExtendedCashRegister` class. The new class will include separate methods for processing payments with different coin types. Additionally, to avoid precision loss with monetary values, the project will utilize `BigDecimal` instead of `double` for representing amounts.

## Objective

Create a Java program that:

- Defines an `ExtendedCashRegister` class that extends the functionality of the original `CashRegister`.
- Implements methods for payment using different coin types:
    - `payDollars(int dollars)`
    - `payQuarters(int quarters)`
    - `payDimes(int dimes)`
    - `payNickles(int nickles)`
    - `payPennies(int pennies)`
- Uses `BigDecimal` to represent monetary values to prevent precision loss.

## ExtendedCashRegister Class Implementation

### Class Definition

The `ExtendedCashRegister` class should include:

- **Instance Variables:**
    - Use `BigDecimal` to represent the total amount of money in the register and the total amount due.

- **Methods:**
    - `public void payDollars(int dollars)`: Accepts dollar payments.
    - `public void payQuarters(int quarters)`: Accepts quarter payments.
    - `public void payDimes(int dimes)`: Accepts dime payments.
    - `public void payNickles(int nickles)`: Accepts nickel payments.
    - `public void payPennies(int pennies)`: Accepts penny payments.
    - `public BigDecimal giveChange()`: Calculates and returns the change due.

### Example Implementation

```java
import java.math.BigDecimal;

public class ExtendedCashRegister {
    private BigDecimal totalDue;
    private BigDecimal totalPaid;

    public ExtendedCashRegister() {
        totalDue = BigDecimal.ZERO;
        totalPaid = BigDecimal.ZERO;
    }

    public void recordPurchase(double amount) {
        totalDue = totalDue.add(BigDecimal.valueOf(amount));
    }

    public void payDollars(int dollars) {
        totalPaid = totalPaid.add(BigDecimal.valueOf(dollars));
    }

    public void payQuarters(int quarters) {
        totalPaid = totalPaid.add(BigDecimal.valueOf(quarters * 0.25));
    }

    public void payDimes(int dimes) {
        totalPaid = totalPaid.add(BigDecimal.valueOf(dimes * 0.10));
    }

    public void payNickles(int nickles) {
        totalPaid = totalPaid.add(BigDecimal.valueOf(nickles * 0.05));
    }

    public void payPennies(int pennies) {
        totalPaid = totalPaid.add(BigDecimal.valueOf(pennies * 0.01));
    }

    public BigDecimal giveChange() {
        return totalPaid.subtract(totalDue);
    }
}
```

### ExtendedCashRegisterTest Class

Create a test class named `ExtendedCashRegisterTest` to test all methods of the `ExtendedCashRegister` class.

```java
public class ExtendedCashRegisterTest {
    public static void main(String[] args) {
        ExtendedCashRegister register = new ExtendedCashRegister();
        register.recordPurchase(0.75);
        register.recordPurchase(1.50);
        register.payDollars(2);
        register.payDimes(3);
        
        System.out.println("Change: ");
        System.out.println(register.giveChange());
        System.out.println("Expected: 0.05");
    }
}
```

## Hints

- Ensure that all payment methods correctly update the total amount paid.
- Use `BigDecimal` for all monetary calculations to avoid precision issues.
- Test the program with various inputs to ensure accuracy in calculating change.

## Notes

- Document your code with comments to explain the functionality of each method.
- Validate the input for payment methods to ensure that negative values are not accepted.

Happy coding! 🎉