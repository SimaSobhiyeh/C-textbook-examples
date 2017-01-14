# C-textbook-examples

#include <iostream>
#include <iomanip>
#include <chrono>
#include <time.h>
#include <Windows.h>
#include <cstdlib>
using namespace std;

void moveTortoise(int *);
void moveHare(int *);

const int totalSquares = 30;

int main()
{
	int T = 1;
	int H = 1;
	bool win = 0;
	bool win_H = 0;
	bool win_T = 0;
	cout << "BANG !!!!! \n AND THEY'RE OFF !!!!! \n \n";
	while (win == 0)
	{
		Sleep(1000);
		moveTortoise(&T);
		moveHare(&H);
		win_H = (H == totalSquares);
		win_T = (T == totalSquares);
		win = win_H || win_T;
		if (win == 0)
		{
			if (H > T)
				cout << setw(T) << "T" << setw(H - T) << 'H' << setw(totalSquares - H) << '\n';
			if (H < T)
				cout << setw(H) << 'H' << setw(T - H) << 'T' << setw(totalSquares - T) << '\n';
			if (H == T)
				cout << setw(H+6) << "OUCH!!!" << '\n';
		}
		if (win == 1)
		{
			if (win_H==1 && win_T==0)
				cout << "Hare wins. Yuch. \n";
			if (win_H==0 && win_T==1)
				cout << "TORTOISE WINS!!! YAY!!! \n";
			if (win_H==1 && win_T==1)
				cout << "It's a tie. \n";
		}
	}
}

void moveTortoise(int *ptrT)
{
	int rnd = 1 + rand() % 10;
	if (0 < rnd && rnd < 6)
		*ptrT = *ptrT + 3;
	if (5 < rnd && rnd < 8)
		*ptrT = *ptrT - 6;
	if (7 < rnd && rnd < 11)
		*ptrT = *ptrT + 1;
	if (*ptrT < 1)
		*ptrT = 1;
	if (*ptrT>totalSquares)
		*ptrT = totalSquares;
}
void moveHare(int *ptrH)
{
	int rnd = 1 + rand() % 10;
	if (2 < rnd && rnd < 5)
		*ptrH = *ptrH + 9;
	if (4 < rnd && rnd < 6)
		*ptrH = *ptrH - 12;
	if (5 < rnd && rnd < 9)
		*ptrH = *ptrH + 1;
	if (8 < rnd && rnd < 11)
		*ptrH = *ptrH - 2;
	if (*ptrH < 1)
		*ptrH = 1;
	if (*ptrH>totalSquares)
		*ptrH = totalSquares;
}
