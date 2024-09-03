# oops-bank
#include <iostream>
using namespace std;

class bank {
public:
    string name;
    int accountno;
    int amount;

    void accept();
    void display();
    void withdraw();
    void deposit();
};

bank b[100];
int j = 0; // Initialize to keep track of the number of accounts

void bank::accept() {
    cout << "Enter your name: ";
    cin >> name;
    cout << "Enter account number: ";
    cin >> accountno;
    cout << "Enter amount: ";
    cin >> amount;
}

void bank::display() {
    cout << "Name: " << name << endl;
    cout << "Account Number: " << accountno << endl;
    cout << "Amount: " << amount << endl;
}

void bank::withdraw() {
    int withdrawAmount;
    int an;
    cout << "Enter your account number: ";
    cin >> an;  // an means account number
    cout << "Enter amount to withdraw: ";
    cin >> withdrawAmount; // withdrawAmount

    for (int i = 0; i < j; i++) {
        if (b[i].accountno == an) {
            if (b[i].amount >= withdrawAmount) {
                b[i].amount -= withdrawAmount;
                cout << "Withdrawal successful. New balance: " << b[i].amount << endl;
            } else {
                cout << "Insufficient funds!" << endl;
            }
            return;
        }
    }
    cout << "Account not found!" << endl;
}

void bank::deposit() {
    int depositAmount;
    int ao;
    cout << "Enter account number: ";
    cin >> ao; // means account number
    cout << "Enter amount to deposit: ";
    cin >> depositAmount; // means deposit

    for (int i = 0; i < j; i++) {
        if (b[i].accountno == ao) {
            b[i].amount += depositAmount;
            cout << "Deposit successful. New balance: " << b[i].amount << endl;
            return;
        }
    }
    cout << "Account not found!" << endl;
}

int main() {
    int choice;

    while (true) {
        cout << "\n1. Accept\n2. Display\n3. Withdraw\n4. Deposit\n5. Exit" << endl;
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                b[j].accept();
                j++; // Increment the number of accounts
                break;
            case 2:
                {
                    int accountNo;
                    cout << "Enter account number: ";
                    cin >> accountNo;

                    bool found = false;
                    for (int i = 0; i < j; i++) {
                        if (b[i].accountno == accountNo) {
                            b[i].display();
                            found = true;
                            break;
                        }
                    }
                    if (!found) {
                        cout << "Account not found!" << endl;
                    }
                }
                break;
            case 3:
                b[0].withdraw(); // Assuming you want to apply it to the first account or handle it properly
                break;
            case 4:
                b[0].deposit(); // Assuming you want to apply it to the first account or handle it properly
                break;
            case 5:
                return 0;
            default:
                cout << "Invalid choice" << endl;
        }
    }

    return 0;
}
