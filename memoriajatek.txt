#include <iostream>
#include <cstdlib>

int main(int argc, char* argv[]) {

	int valtozok[5] = {1, 2, 3, 4, 5};
	int* pointerek[5] = {nullptr};
	int i = 0;
	int pontok = 0;
	int valtozo;
	int pointer;

	while (i < 5) { //pointerek feltoltese veletlenszeruen

		int veletlenSzam = rand() % 5;

		if (pointerek[veletlenSzam] != nullptr) {
			veletlenSzam = rand() % 5;
		}
		else {
			pointerek[veletlenSzam] = &valtozok[i];
			i += 1;
		}
	}

	std::cout << "Udv a jatekban! 1-2-3-4-5 szamokkal tud valaszolni a kerdesekre. Sok szerencset!" << std::endl;

	while (pontok < 5) {

		std::cout << "Valassz egy valtozot!" << std::endl; //Valtozo input
		for (int i = 0; i < 5; i++) {
			if (valtozok[i] > 0) {
				std::cout << valtozok[i] << ". " << valtozok[i] << std::endl;
			}
		}
		std::cin >> valtozo;
		std::cout << "memoriacim: " << &valtozok[valtozo - 1] << std::endl;

		std::cout << "Valassz egy pointert!" << std::endl; //Pointer input
		for (int i = 0; i < 5; i++) {
			if (pointerek[i] != nullptr) {
				std::cout << i+1 << ". " << "p" << i + 1 << std::endl;
			}	
		}
		std::cin >> pointer;
		std::cout << "memoriacim: " << pointerek[pointer - 1] << std::endl;

		if (&valtozok[valtozo - 1] == pointerek[pointer - 1]) { //Talalt

			pontok += 1;
			std::cout << "Megvan a(z) " << pontok << ". par! ";

			valtozok[valtozo - 1] = 0;
			pointerek[pointer - 1] = nullptr;
		}
		else {													//Nem talalt
			std::cout << "Sajnos ez nem talalt...  ";
		}
	}
	std::cout << "Gratulalok! Nyertel!!!";
}