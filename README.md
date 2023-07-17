# week-12-
Scripts for week 12
class Bank:
    def __init__(self):
        self.accounts = []

    def add_account(self, account):
        self.accounts.append(account)

    def __str__(self):
        sorted_accounts = sorted(self.accounts, key=lambda acc: acc.get_name())
        return '\n'.join(str(account) for account in sorted_accounts)


class SavingsAccount:
    def __init__(self, name, balance=0):
        self.name = name
        self.balance = balance

    def deposit(self, amount):
        self.balance += amount

    def withdraw(self, amount):
        if self.balance >= amount:
            self.balance -= amount
        else:
            print("Insufficient funds")

    def get_name(self):
        return self.name

    def __str__(self):
        return f"Account Name: {self.name}\nBalance: ${self.balance}"


bank = Bank()
account1 = SavingsAccount("John Doe", 500)
account2 = SavingsAccount("Alice Smith", 1000)
account3 = SavingsAccount("Bob Johnson", 750)

bank.add_account(account1)
bank.add_account(account2)
bank.add_account(account3)

print(bank)  # Displays the accounts in order of name

import tkinter as tk
from tkinter import messagebox

class ATM:
    def __init__(self, master):
        self.master = master
        self.login_attempts = 0
        self.login_button = tk.Button(self.master, text="Login", command=self.login)
        self.login_button.pack()

    def login(self):
        password = "1234"  # Replace with the actual password
        entered_password = "1234"  # Replace with the entered password
        if entered_password == password:
            messagebox.showinfo("Success", "Login Successful")
            self.login_attempts = 0  # Reset login attempts
            self.login_button.config(state=tk.NORMAL)  # Enable login button
        else:
            self.login_attempts += 1
            if self.login_attempts == 3:
                messagebox.showwarning("Warning", "Police will be called")
                self.login_button.config(state=tk.DISABLED)  # Disable login button

root = tk.Tk()
atm = ATM(root)
root.mainloop()
