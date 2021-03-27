Покрытие отрезками точки

По данным n отрезкам необходимо найти множество точек минимального размера, для которого каждый из отрезков содержит хотя бы одну из точек.В первой строке дано число 1 ≤ n ≤ 100 отрезков. Каждая из последующих n строк содержит по два числа 0 ≤ l ≤ r ≤ 10^9, задающих начало и конец отрезка. Выведите оптимальное число mm точек и сами m точек. Если таких множеств точек несколько, выведите любое из них.

#include <iostream>
#include <vector>
#include <list>
#include <algorithm>

bool pred(std::pair<int, int> a, std::pair<int, int> b) {
	return a.second < b.second;
}

int main(void) {
	int segment_count = 0;
	std::cin >> segments_count
	std::list<std::pair <int, int>> segments;
	for (size_t i = 0; i < segments_count; ++i) {
		int l = 0, r = 0;
		std::cin >> l >> r;
		segments.push_back(std::make_pair(l, r));
	}
	segments.sort([](const std::pair <int, int> &l, const std::pair <int, int> &r) { return l.second < r.second;});
	std::vector <int> points;
	while (0 != segments.size()) {
		int p = (*segments.begin()).second;
		points.push_back(p);
		while (true) {
			if (segments.size() != 0 && (*segments.begin()).first <= p) segments.pop_front();
			else break; 
		}
	}
	size_t points_count = points.size();
	std::cout << points_count << std::endl;
	for (auto pt : points) std::cout << pt << " ";
	std::cout << std::endl;
  return 0;
}
