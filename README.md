
# Dart OOP Assignment: Kigali Bus Card

**Name:** Mukiza Nseko Gervais  
**Student ID:** 26443/2024

## My numbers

- D = 73
- L = 3
- Starting balance = 1730 RWF
- Bus fare = 273 RWF
- Student discount = 13%

## Output of main.dart

PS D:\GitHub\dart-oop-26443> dart run bug_hunt.dart
Error: name too short
Owner: Ama | Balance: 1730 RWF
Owner: Mukiza Nseko Gervais | Balance: 1730 RWF
Error: top-up must be 500 to 50000 RWF
Topped up 2000 RWF
Paid 273 RWF
Paid 273 RWF
Owner: Mukiza Nseko Gervais | Balance: 3184 RWF
Student discount: 35 RWF
Paid 238 RWF
Owner: Mukiza Nseko Gervais | Balance: 1492 RWF
Student card: 13% off


## Part 1: Why no setter for balance?

I did not add a direct setter for the balance because it could allow someone to change the balance to an invalid amount. The topUp() and pay() methods control balance changes and make sure the card follows the rules.

## Part 2: What does ~/ do?

The / operator performs normal division and returns a decimal result. For example, 237 * 17 / 100 gives 40.29.

The ~/ operator performs integer division. It removes the decimal part and returns a whole number. For example, 237 * 17 ~/ 100 gives 40.

This is useful when calculating the student discount because the discount is stored as a whole number of RWF.

## Part 4: Bug table

| Bug | The line | Why it is wrong (my words) | My fix |
|---|---|---|---|
| 1 | Lines 2–3: _brand and _battery | Dart needs starting values for these non-nullable fields. | I initialized them to '' and 0. |
| 2 | SmartPhone constructor | The Phone constructor needs brand and battery, but the child constructor does not pass them to the parent. | I added : super(brand, battery). |
| 3 | @override above restart() | The parent Phone class does not have a restart() method to override. | I added a restart() method to Phone. |
| 4 | Missing setter in Phone | I assigned p.battery, but Phone only had a getter. | I added a setter that accepts values from 0 to 100. |
| 5 | print(p.battery()); | battery is a getter, not a method. | I changed it to print(p.battery);. |
| Not a bug | p.battery = 100; | This is valid after adding the setter, and 100 is an allowed value. | No fix was needed. |

### Output after fixing


100


## Part 5: Prediction

### My prediction

I think the first output will be 1. The bag starts at 0, and add() increases the number of items by 1. Setting the count to -5 will be ignored because the setter only accepts values greater than or equal to 0.

I think the second output will be 5. Each BigBag.add() call adds two items because it calls super.add() twice. After calling it two times, the count becomes 4. The next statement adds 1, making the count 5.

### Actual output

1
5

### Was I right?

Yes, my predictions were correct. The program printed 1 and then 5, just as I expected.
