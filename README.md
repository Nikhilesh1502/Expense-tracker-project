import time

expenses = []

def add_expense():
    try:
        name = input("Enter expense name (default: 'Unknown'): ") or "Unknown"
        amount = float(input("Enter amount (default: 0.0): ") or 0.0)
        category = input("Enter category (default: 'Misc'): ") or "Misc"
        expenses.append({"name": name, "amount": amount, "category": category})
        print("Expense added successfully!\n")
    except ValueError:
        print("Invalid amount. Please enter a number.\n")

def view_expenses():
    if not expenses:
        print("No expenses recorded.\n")
        return
    print("\nExpense List:")
    for i, expense in enumerate(expenses, start=1):
        print(f"{i}. {expense['name']} - ${expense['amount']} ({expense['category']})")
    print()

def analyze_expenses():
    if not expenses:
        print("No expenses to analyze.\n")
        return
    total = sum(exp['amount'] for exp in expenses)
    print(f"\nTotal Expenses: ${total:.2f}\n")

def main():
    while True:
        try:
            print("1. Add Expense")
            print("2. View Expenses")
            print("3. Analyze Expenses")
            print("4. Exit")
            choice = input("Enter your choice: ")

            if choice == '1':
                add_expense()
            elif choice == '2':
                view_expenses()
            elif choice == '3':
                analyze_expenses()
            elif choice == '4':
                print("Exiting program.")
                break
            else:
                print("Invalid choice. Please enter a number between 1-4.\n")

            time.sleep(1)  # Small delay to prevent session timeouts
        except Exception as e:
            print(f"An error occurred: {e}. Restarting...\n")

if __name__ == "__main__":
    main()
