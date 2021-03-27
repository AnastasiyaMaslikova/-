Непрерывный рюкзак

Первая строка содержит количество предметов 1 ≤ n ≤ 10^3 и вместимость рюкзака 0 ≤ W ≤2⋅10^6. Каждая из следующих n строк задаёт стоимость 0 ≤ ci ≤ 2⋅10^6 и объём  0 < wi ≤ 2⋅10^6 предмета (n, W, ci, wi — целые числа). Выведите максимальную стоимость частей предметов (от каждого предмета можно отделить любую часть, стоимость и объём при этом пропорционально уменьшатся), помещающихся в данный рюкзак, с точностью не менее трёх знаков после запятой.

#include <iostream>
#include <algorithm>
#include <cassert>
#include <vector>
#include <cinttypes>
#include <ios>
	
struct Item final {
  int weight;
  int value;
};
double get_max_knapsack_value(int capacity, std::vector <Item> items) {
  std::sort(items.begin(), items.end(), [](const Item &lhs, const Item &rhs) {
      return static_cast<std::int64_t>(lhs.weight) * rhs.value <
             static_cast<std::int64_t>(rhs.weight) * lhs.value;
  });
    double value = 0.0;
  for (auto &item:items) {
    if (capacity > item.weight) {
      capacity -= item.weight;
      value += item.value;
    } else {
      value += item.value * (static_cast <double>(capacity) / item.weight);
      break;
    }
  }
  return value;
}
int main(void) {
  std::ios_base::sync_with_stdio(false); 
  int number_of_items;
  int knapsack_capacity;
  std::cin >> number_of_items >> knapsack_capacity;
  std::vector <Item> items(number_of_items);
  for (int i = 0; i < number_of_items; i++) {
    std::cin >> items[i].value >> items[i].weight;
  }
  double max_knapsack_value = get_max_knapsack_value(knapsack_capacity, std::move(items));
  std::cout.precision(10);
  std::cout << max_knapsack_value << std::endl;
  return 0;
} 
