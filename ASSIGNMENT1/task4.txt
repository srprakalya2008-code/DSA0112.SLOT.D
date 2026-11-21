
#include <iostream>
#include <iomanip>
#include <limits>
using namespace std;

int main() {
    int a = 7, b = 2;

    // Implicit integer division followed by conversion to double
    double c = a / b;

    // Explicit conversion before division
    double d = static_cast<double>(a) / b;

    cout << c << " " << d << '\n';

    // Character promotion to int
    char ch = 'A' + 2;
    cout << ch << " " << ch + 1 << '\n';

    // Integer to bool conversion
    bool flag = 5;
    cout << flag << " " << boolalpha << flag << '\n';

    // Signed and unsigned comparison
    unsigned int u = 1;
    int s = -1;
    cout << (s < u ? "s < u" : "s >= u") << '\n';

    // Explicit conversion examples
    double value = 9.8;
    int converted = static_cast<int>(value);
    cout << "Explicit conversion: " << converted << '\n';

    // Brace initialization prevents narrowing
    int validNumber{3};
    cout << "Brace initialization: " << validNumber << '\n';

    // Demonstrate overflow-safe range information
    cout << "Maximum int: "
         << numeric_limits<int>::max() << '\n';

    return 0;
}
