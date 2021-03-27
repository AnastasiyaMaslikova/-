Декодирование Хаффмана

Восстановите строку по её коду и беспрефиксному коду символов. 

В первой строке входного файла заданы два целых числа k и l через пробел — количество различных букв, встречающихся в строке, и размер получившейся закодированной строки, соответственно. В следующих k строках записаны коды букв в формате "letter: code". Ни один код не является префиксом другого. Буквы могут быть перечислены в любом порядке. В качестве букв могут встречаться лишь строчные буквы латинского алфавита; каждая из этих букв встречается в строке хотя бы один раз. Наконец, в последней строке записана закодированная строка. Исходная строка и коды всех букв непусты. Заданный код таков, что закодированная строка имеет минимальный возможный размер.

В первой строке выходного файла выведите строку ss. Она должна состоять из строчных букв латинского алфавита. Гарантируется, что длина правильного ответа не превосходит 10^4 символов.

#include <iostream>
#include <string>
#include <unordered_map>

int main() {
	int letter_num = 0, code_line_size = 0;
	std::cin >> letter_num >> code_line_size;
	std::unordered_map<std::string, char> huffman_map;
	for (int i = 0; i < letter_num; ++i) {
		std::string code;
		std::getline(std::cin, code);
		if (code.size() < 4) { --i; continue; }
		char ch = code[0];
		std::string cd = code.substr(3, code.size());
		huffman_map.insert(std::pair<std::string, char>(cd, ch));
	}
	std::string code_line;
	std::getline(std::cin, code_line);
	std::string code;
	for (auto ch : code_line) {
		code += ch;
		if (huffman_map.find(code) != huffman_map.end()) {
			std::cout << huffman_map.at(code);
			code.erase();
		}
	}
	return 0;
}
