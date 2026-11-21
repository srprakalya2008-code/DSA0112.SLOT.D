
#include <iostream>
#include <iomanip>
#include <limits>
#include <cmath>
using namespace std;

int main() {
    // Representative fare for testing: Rs. 12.34
    constexpr long long FARE_PAISE = 1234;
    constexpr double FARE_RUPEES = 12.34;

    long long journeyCounts[] = {
        20000, 500000, 3000000
    };

    cout << "NAMMA METRO - TOTAL FARE COMPARISON\n";
    cout << "Representative fare: Rs. 12.34\n\n";

    cout << fixed << setprecision(2);

    for (long long journeys : journeyCounts) {
        // Exact integer-paise calculation
        long long totalPaise = journeys * FARE_PAISE;

        // Floating-point calculation
        double totalDouble = journeys * FARE_RUPEES;

        // Compare totals in rupees
        double integerPaiseRupees = totalPaise / 100.0;
        double difference =
            totalDouble - integerPaiseRupees;

        cout << "Journeys: " << journeys << '\n';

        cout << "Integer-paise total: Rs. "
             << integerPaiseRupees << '\n';

        cout << "Double total:         Rs. "
             << totalDouble << '\n';

        cout << "Difference:           Rs. "
             << difference << '\n';

        // Check whether total paise fits in a typical 32-bit int
        long long intMax = numeric_limits<int>::max();

        if (totalPaise > intMax) {
            cout << "Int paise total: OVERFLOW RISK\n";
        } else {
            cout << "Int paise total: "
                 << totalPaise << '\n';
        }

        cout << "Long long paise total: "
             << totalPaise << '\n';

        cout << "-----------------------------------\n";
    }

    // Demonstrate the limits of int
    cout << "\nDATA TYPE LIMITS\n";
    cout << "Maximum int: "
         << numeric_limits<int>::max() << '\n';

    cout << "Maximum long long: "
         << numeric_limits<long long>::max() << '\n';

    // Demonstrate floating-point representation
    double test = 0.1 + 0.2;

    cout << setprecision(17);
    cout << "\nFloating-point test (0.1 + 0.2): "
         << test << '\n';

    return 0;
}
