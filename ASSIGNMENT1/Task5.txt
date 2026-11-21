
#include <iostream>
using namespace std;

// Peak-hour check
bool isPeakHour(int hour) {
    return (hour >= 8 && hour < 10) ||
           (hour >= 17 && hour < 20);
}

// Calculate fare after peak surcharge
int applySurcharge(int fare, bool peak) {
    return peak ? fare * 120 / 100 : fare;
}

// Apply passenger concession
int applyConcession(int fare, int concessionPercent) {
    return fare * (100 - concessionPercent) / 100;
}

int main() {
    int x = 5, y = 3;

    cout << x + y * 2 << " ";
    cout << (x + y) * 2 << '\n';

    cout << (x > y ? x : y) << " ";
    cout << x % 4 * 2 << '\n';

    cout << 10 / 3 << " ";
    cout << 10 % 3 << " ";
    cout << -10 / 3 << " ";
    cout << -10 % 3 << '\n';

    int k = 0;

    for (int i = 0; i < 10; i += 3)
        k += i;

    cout << k << '\n';

    // Fare expression examples
    int hour = 8;
    int baseFare = 2000; // Rs. 20 in paise
    int concessionPercent = 50;

    bool peak = isPeakHour(hour);

    int fareAfterSurcharge = applySurcharge(baseFare, peak);
    int finalFare = applyConcession(
        fareAfterSurcharge, concessionPercent
    );

    cout << "Peak hour: " << boolalpha << peak << '\n';
    cout << "Base fare in paise: " << baseFare << '\n';
    cout << "Fare after surcharge in paise: "
         << fareAfterSurcharge << '\n';
    cout << "Final fare in paise: " << finalFare << '\n';

    return 0;
}
