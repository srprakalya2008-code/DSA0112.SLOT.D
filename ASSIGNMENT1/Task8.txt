#include <iostream>
#include <iomanip>
#include <limits>
#include <string>
using namespace std;

constexpr long long MIN_BALANCE_PAISE = 5000;

bool readNumber(const string& prompt, long long& value) {
    while (true) {
        cout << prompt;

        if (cin >> value) {
            return true;
        }

        if (cin.eof()) {
            return false;
        }

        cout << "Invalid input! Please enter a number.\n";

        cin.clear();
        cin.ignore(numeric_limits<streamsize>::max(), '\n');
    }
}

void printMoney(long long paise) {
    cout << "Rs. " << fixed << setprecision(2)
         << paise / 100.0;
}

int main() {
    string cardId;
    long long balance, fare, journeyCount = 0;

    cout << "NAMMA METRO SMART-CARD SYSTEM\n";

    cout << "Enter Card ID: ";
    if (!(cin >> cardId)) {
        cout << "Invalid card ID input.\n";
        return 1;
    }

    if (!readNumber("Enter initial balance in paise: ", balance)) {
        cout << "Input ended unexpectedly.\n";
        return 1;
    }

    if (balance < 0) {
        cout << "Balance cannot be negative.\n";
        return 1;
    }

    while (true) {
        if (!readNumber(
                "Enter fare in paise (0 to finish): ", fare)) {
            cout << "\nInput ended unexpectedly.\n";
            break;
        }

        if (fare == 0) {
            break;
        }

        if (fare < 0) {
            cout << "Fare cannot be negative. Try again.\n";
            continue;
        }
        if (balance < fare ||
            balance - fare < MIN_BALANCE_PAISE) {
            cout << "Journey denied: minimum balance "
                 << "of Rs. 50 must remain.\n";
            continue;
        }

        balance -= fare;
        journeyCount++;

        cout << "Journey accepted. Fare: ";
        printMoney(fare);
        cout << '\n';

        cout << "Remaining balance: ";
        printMoney(balance);
        cout << "\n";
    }

    cout << "\n========== JOURNEY REPORT ==========\n";
    cout << "Card ID: " << cardId << '\n';
    cout << "Successful journeys: " << journeyCount << '\n';
    cout << "Final balance: ";
    printMoney(balance);
    cout << "\n====================================\n";

    return 0;
}
