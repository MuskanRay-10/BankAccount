# BankAccount
# A program that Creates a BankAccount object, Prompts the user to enter account details and initial balance, allows the user to perform deposit and withdrawal operations, displays the final balance

#include <iostream>
#include <string>

class BankAccount {
private:
    int accountNumber;
    double balance;
    std::string accountHolderName;

public:
    // Constructor to initialize account details
    BankAccount(int accNum, double initialBalance, std::string holderName) 
        : accountNumber(accNum), balance(initialBalance), accountHolderName(holderName) {}

    // Deposit method
    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            std::cout << "Deposited: $" << amount << std::endl;
        } else {
            std::cout << "Invalid deposit amount!" << std::endl;
        }
    }

    // Withdraw method
    void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            std::cout << "Withdrawn: $" << amount << std::endl;
        } else {
            std::cout << "Insufficient funds or invalid amount!" << std::endl;
        }
    }

    // Display balance
    void displayBalance() const {
        std::cout << "Current Balance: $" << balance << std::endl;
    }
};

int main() {
    int accNumber;
    double initialBalance;
    std::string holderName;

    // Getting user input
    std::cout << "Enter Account Number: ";
    std::cin >> accNumber;
    std::cin.ignore(); // Clear newline left in buffer

    std::cout << "Enter Account Holder Name: ";
    std::getline(std::cin, holderName);

    std::cout << "Enter Initial Balance: ";
    std::cin >> initialBalance;

    // Create a BankAccount object
    BankAccount account(accNumber, initialBalance, holderName);

    // Perform deposit and withdrawal operations
    double amount;
    std::cout << "\nEnter amount to deposit: ";
    std::cin >> amount;
    account.deposit(amount);

    std::cout << "Enter amount to withdraw: ";
    std::cin >> amount;
    account.withdraw(amount);

    // Display final balance
    std::cout << "\nFinal ";
    account.displayBalance();

    return 0;
}
