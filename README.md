# GL_project
GL_project
#include "stdafx.h"
#include <iostream>
#include <windows.h>
#include <conio.h>
using namespace std;
HANDLE H = GetStdHandle(STD_OUTPUT_HANDLE);
void Stand(int x, int y, int k, char*str){
CONSOLE_CURSOR_INFO ci; ci.bVisible = 0; ci.dwSize = 100; SetConsoleCursorInfo(H, &ci); // забрати мигаючий курсор
setlocale(LC_ALL, "RUS");
COORD c;
c.X = x; c.Y = y;
SetConsoleCursorPosition(H, c);
SetConsoleTextAttribute(H, k);
cout « str « "\n";
}

void main()
{

Stand(5, 5, 10, "Нова гра");

Stand(5, 9, 2, "Опції");
Stand(5, 11, 2, "вихід");

int k; // код клавіші
int cur = 1; // показує який пункт вибрано
while (1){
k = _getch();
if (k == 80){
if (cur<4){
cur++;
if (cur == 2){
Stand(5, 5, 2, "Нова гра");

}
else if (cur == 3){

Stand(5, 9, 10, "Опції");
}
else if (cur == 4){
Stand(5, 9, 2, "опції");
Stand(5, 11, 10, "Вихід");
}
}
}
else if (k == 72){
if (cur>1){
cur--;
if (cur == 3){
Stand(5, 9, 10, "Опції");
Stand(5, 11, 2, "Вихід");
}
else if (cur == 2){

Stand(5, 9, 2, "опції");
}
else if (cur == 1){
Stand(5, 5, 10, "Нова гра");

}
}
}
else if (k == 13){
system("cls");
SetConsoleTextAttribute(H, 12);
if (cur == 1) cout « "Початок нової гри!\n\n";

else if (cur == 3) cout « "Настройки ігри!\n\n";
else cout « "до зустрічі\n\n";
_getch();
exit(0);
}
}

}
