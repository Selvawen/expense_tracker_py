# Expense Tracker

A simple and efficient command-line application for tracking your daily expenses.

## Table of Contents
- [Demo](#demo)
- [Technology Used](#technology-used)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Code Overview](#code-overview)
  - [Expense Class](#expense-class)
  - [ExpenseTracker Class](#expensetracker-class)
    - [Methods](#methods)
  - [Main Function](#main-function)
- [License](#license)

## Demo
![ExpensesPic](https://github.com/Selvawen/expense_tracker_py/assets/111338548/facf35e3-4078-4969-be7d-4bac0b54219f)


## Technology Used
![python 2](https://github.com/Selvawen/guessing-game-py/assets/111338548/2cda6787-fa36-41ca-9b3e-ec739b8d922d)

## Features

- **Add Expense**: Record an expense with the date, description, and amount.
- **Remove Expense**: Delete an expense by its index.
- **View Expenses**: Display a list of all recorded expenses.
- **Total Expenses**: Calculate and display the total amount of all expenses.

## Prerequisites

- Python 3.x

## Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/expense-tracker.git
   ```
2. Navigate to the project directory:
   ```sh
   cd expense-tracker
   ```

## Usage
Run the expense tracker application 

```sh
python expense_tracker.py
```
Follow the on-screen prompts to add, remove, view, and calculate your expenses.

## Code Overview

### Expense Class
This class represents a single expense with three attributes:

- `date`: The date of the expense.
- `description`: A description of the expense.
- `amount`: The amount spent.

```python
class Expense:
    def __init__(self, date, description, amount):
        self.date = date
        self.description = description
        self.amount = amount
```
### ExpenseTracker Class
This class manages a list of expenses and provideds methods to manipulate and view them. 

#### Methods:
- `add_expense(expense)`: Adds an expense to the list.
- `remove_expense(index)`: Removes an expense by its index in the list.
- `view_expenses()`: Displays all recorded expenses.
- `total_expenses()`: Calculates and displays the total amount of all expenses.

```python
class ExpenseTracker:
    def __init__(self):
        self.expenses = []

    def add_expense(self, expense):
        self.expenses.append(expense)

    def remove_expense(self, index):
        if 0 <= index < len(self.expenses):
            del self.expenses[index]
            print("Expense removed successfully.")
        else:
            print("Invalid expense index.")

    def view_expenses(self):
        if len(self.expenses) == 0:
            print("No expenses found.")
        else:
            print("Expense List:")
            for i, expense in enumerate(self.expenses, start=1):
                print(f"{i}. Date: {expense.date}, Description: {expense.description}, Amount: {expense.amount}")

    def total_expenses(self):
        total = sum(expense.amount for expense in self.expenses)
        print(f"Total Expenses: ${total:.2f}")
```
### Main Function
The 'main' function provides a menu-driven interface for interacting with the Expense Tracker. 

```python
def main():
    tracker = ExpenseTracker()

    while True:
        print("\nExpense Tracker Menu:")
        print("1. Add Expense")
        print("2. Remove Expense")
        print("3. View Expenses")
        print("4. Total Expenses")
        print("5. Exit")

        choice = input("Enter your choice (1-5): ")

        if choice == "1":
            date = input("Enter the date (YYYY-MM-DD): ")
            description = input("Enter the description: ")
            amount = float(input("Enter the amount: "))
            expense = Expense(date, description, amount)
            tracker.add_expense(expense)
            print("Expense added successfully.")
        elif choice == "2":
            index = int(input("Enter the expense index to remove: ")) - 1
            tracker.remove_expense(index)
        elif choice == "3":
            tracker.view_expenses()
        elif choice == "4":
            tracker.total_expenses()
        elif choice == "5":
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
```
### License
MIT License

Copyright (c) 2024 Benjamin Anderson

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
