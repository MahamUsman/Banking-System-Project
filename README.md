//# Banking-System-Project
//source code of Banking Sytem
#include <iostream>
#include <conio.h>
#include <string.h>
#include<windows.h>

using namespace std;

class Bank {
private:   // only class member can access
    int total;
    struct Person {
        string name;
        string ID;
        string address;
        long long contact;
        long long cash;
    } person[100];  // Maximum 100 people allowed

public: // Can access any where
    Bank() {
        total = 0;
    }

    void choice();
    void personData();
    void showData();
    void updateData();
    void searchData();
    void transactions();
    void deleteData();
};

int main() {
	system("COLOR 5");
    cout << "************************************************************************************\n"
         << "*                              Bank Management System                              *\n"
         << "************************************************************************************\n\n";

    Bank b; //creating the object of the class
    b.choice();

    return 0;
}

void Bank::choice() { //:: //scope resolution operator
    while (true) { 
        cout << "\n\nChoice Menu:\n"
             << "************************************************************\n"
             << "1. Create a new account\n"
             << "2. View customer's list\n"
             << "3. Update information of an existing account\n"
             << "4. Check the details of an existing account\n"
             << "5. Withdraw or deposit transactions\n"
             << "6. Remove an existing Account\n"
             << "7. Exit\n"
             << "************************************************************\n\n"
             << "Your Choice: ";

        char ch;
        cin >> ch;

        system("CLS"); // cant end

        switch (ch) {
            case '1':
                personData();
                break;
            case '2':
                if (total == 0)
                    cout << "\n************************************************************\n"
                         << "No data is entered\n";
                else
                    showData();
                break;
            case '3':
                if (total == 0)
                    cout << "\n************************************************************\n"
                         << "No data is entered\n";
                else
                    updateData();
                break;
            case '4':
                if (total == 0)
                    cout << "\n************************************************************\n"
                         << "No data is entered\n";
                else
                    searchData();
                break;
            case '5':
                if (total == 0)
                    cout << "\n************************************************************\n"
                         << "No data is entered\n";
                else
                    transactions();
                break;
            case '6':
                if (total == 0)
                    cout << "\n************************************************************\n"
                         << "No data is entered\n";
                else
                    deleteData();
                break;
            case '7':
                cout << "\n************************************************************\n"
                     << "        Thanks for Using our Software! \n"
                     << "\n************************************************************\n";
                exit(0);
            default:
                cout << "Invalid input\n";
        }
    }
}

void Bank::personData() { // fUNCTION OF A CLASS 
    cout << "***************************************************************\n"
         << "              Creating new account \n"
         << "***************************************************************\n\n";

    cout << "Enter data of a person " << total + 1 << endl
         << "*********************************************************\n"
         << "Person name            :  ";
    cin.ignore();
    getline(cin, person[total].name); //Name is stored in the name part of the person object at position total.

    cout << "ID                     :  ";
    cin >> person[total].ID;

    cout << "Address                :  ";
    cin.ignore();  /// Read the space in the program
    getline(cin, person[total].address);

    cout << "Contact                :  ";
    cin >> person[total].contact;

    cout << "Cash                   :  ";
    cin >> person[total].cash;

    cout << "***************************************************************\n";

    total++;  // Increment

    cout << "Data entered successfully!\n\n\n";
}

void Bank::showData() {
    cout << "***************************************************************\n"
         << "              Record list of account holders \n"
         << "***************************************************************\n\n";

    for (int i = 0; i < total; i++) {
        cout << "Data of person " << i + 1 << endl
             << "*********************************************************\n"
             << "Name                :  " << person[i].name << endl
             << "ID                  :  " << person[i].ID << endl
             << "Address             :  " << person[i].address << endl
             << "Contact             :  " << person[i].contact << endl
             << "Cash                :  " << person[i].cash << endl
             << "***************************************************************\n";
    }
}

void Bank::updateData() {
    cout << "***************************************************************\n"
         << "              Updating data of an existing account \n"
         << "***************************************************************\n\n";

    cout << "Enter ID of the person whose data you want to update: ";
    string id;
    cin >> id;

    for (int i = 0; i < total; i++) {
        if (id == person[i].ID) {
            cout << "\n\nPrevious Data of person " << i + 1 << endl
                 << "*********************************************************\n"
                 << "Name                :  " << person[i].name << endl
                 << "ID                  :  " << person[i].ID << endl
                 << "Address             :  " << person[i].address << endl
                 << "Contact             :  " << person[i].contact << endl
                 << "Cash                :  " << person[i].cash << endl
                 << "***************************************************************\n\n\n";

            cout << "Enter updated data for person " << i + 1 << endl
                 << "*********************************************************\n"
                 << "Person name         :  ";
            cin.ignore();
            getline(cin, person[i].name);

            cout << "ID                  :  ";
            cin >> person[i].ID;

            cout << "Address             :  ";
            cin.ignore();
            getline(cin, person[i].address);

            cout << "Contact             :  ";
            cin >> person[i].contact;

            cout << "Cash                :  ";
            cin >> person[i].cash;

            cout << "***************************************************************\n";
            return;
        }
    }

    cout << "\n************************************************************\n"
         << "No record found with ID: " << id << endl;
}

void Bank::searchData() {
    cout << "***************************************************************\n"
         << "              Search data of an account holder \n"
         << "***************************************************************\n\n";

    cout << "Enter ID of the person whose data you want to search: ";
    string id;
    cin >> id;

    for (int i = 0; i < total; i++) {
        if (id == person[i].ID) {
            cout << "\n\nData of person " << i + 1 << endl
                 << "*********************************************************\n"
                 << "Name                :  " << person[i].name << endl
                 << "ID                  :  " << person[i].ID << endl
                 << "Address             :  " << person[i].address << endl
                 << "Contact             :  " << person[i].contact << endl
                 << "Cash                :  " << person[i].cash << endl
                 << "***************************************************************\n";
            return;
        }
    }

    cout << "\n************************************************************\n"
         << "No record found with ID: " << id << endl;
}

void Bank::transactions() {
    cout << "***************************************************************\n"
         << "              Transactions of an account holder \n"
         << "***************************************************************\n\n";

    cout << "Enter ID of the person for transactions: ";
    string id;
    cin >> id;

    for (int i = 0; i < total; i++) {
        if (id == person[i].ID) {
            cout << "\n\nData of person " << i + 1 << endl
                 << "*********************************************************\n"
                 << "Name                :  " << person[i].name << endl
                 << "Address             :  " << person[i].address << endl
                 << "Contact             :  " << person[i].contact << endl
                 << "Existing Cash       :  " << person[i].cash << " Rupees\n"
                 << "***************************************************************\n";

            cout << "\n\nChoice Menu:\n"
                 << "************************************************************\n"
                 << "1. Deposit amount\n"
                 << "2. Withdraw amount\n"
                 << "************************************************************\n"
                 << "Your Choice: ";

            char ch;
            cin >> ch;

            switch (ch) {
                case '1':
                    cout << "\n\n     Deposit amount \n"
                         << "***************************************************************\n";
                    cout << "How much cash you want to deposit: ";
                    long long cash_deposit;
                    cin >> cash_deposit;
                    person[i].cash += cash_deposit;
                    cout << "Your new cash: " << person[i].cash << " Rupees\n"
                         << "***************************************************************\n";
                    return;
                case '2':
                    cout << "\n\n     Withdraw amount \n"
                         << "***************************************************************\n";
                    cout << "How much cash you want to withdraw: ";
                    long long cash_withdraw;
                    cin >> cash_withdraw;
                    if (cash_withdraw > person[i].cash) {
                        cout << "Insufficient balance!\n";
                        return;
                    }
                    person[i].cash -= cash_withdraw;
                    cout << "Your new cash: " << person[i].cash << " Rupees\n"
                         << "***************************************************************\n";
                    return;
                default:
                    cout << "Invalid input\n";
                    return;
            }
        }
    }

    cout << "\n************************************************************\n"
         << "No record found with ID: " << id << endl;
}

void Bank::deleteData() {
    cout << "***************************************************************\n"
         << "              Removing/Deleting an account from record list \n"
         << "***************************************************************\n\n";

    cout << "\nChoice Menu:\n"
         << "************************************************************\n"
         << "1. Remove specific person account from record list\n"
         << "2. Remove full record list of account holders\n"
         << "************************************************************\n"
         << "Your Choice: ";

    char ch;
    cin >> ch;

    switch (ch) {
        case '1': {
            cout << "\nEnter ID of the person whose data you want to remove: ";
            string id;
            cin >> id;

            for (int i = 0; i < total; i++) {
                if (id == person[i].ID) {
                    for (int j = i; j < total - 1; j++) {
                        person[j] = person[j + 1];
                    }
                    total--;
                    cout << "\n************************************************************\n"
                         << "Record with ID " << id << " has been deleted\n";
                    return;
                }
            }

            cout << "No record found with ID: " << id << endl;
            break;
        }
        case '2':
            total = 0;
            cout << "\n************************************************************\n"
                 << "All records have been deleted\n";
            break;
        default:
            cout << "\nInvalid Input\n";
            break;
    }
}

