Различные слагаемые

По данному числу 1 ≤ n ≤ 10^9 найдите максимальное число k, для которого nn можно представить как сумму k различных натуральных слагаемых. Выведите в первой строке число k, во второй — k слагаемых.

#include <iostream>
#include <cmath>

int main() {
        int number = 0;
        std::cin >> n;
	double k1 = (-1.0 + std::sqrt(1.0 + 8.0 * ((double)n))) / 2.0;
	int k = (int)k1;
	std::cout << k << std::endl;
	for (int i = 1; i <= k - 1; ++i) std::cout << i << " ";
	std::cout << (n - (k - 1) * k / 2) << std::endl;
        return 0;
}
