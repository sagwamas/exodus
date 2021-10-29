// # exodus
// 미로게임
#include<stdio.h>
// _getch를 사용하기위한 헤더파일
#include<conio.h>
// gotoxy문을 사용하기위한 헤더파일
#include<windows.h>
// 시간
#include<stdlib.h>

int map[20][20] = { { 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1 },
					{ 1,0,1,0,0,0,0,0,1,1,0,0,0,0,0,1,0,0,0,1 },
					{ 1,0,1,0,1,0,1,0,0,0,0,1,0,1,0,1,0,1,0,1 },
					{ 1,0,1,0,1,0,1,1,1,1,1,1,0,1,1,1,0,1,1,1 },
					{ 1,0,1,0,1,1,1,1,0,0,0,1,0,0,0,0,0,0,0,1 },
					{ 1,0,1,0,0,1,0,0,0,1,1,1,1,0,1,1,1,1,0,1 },
					{ 1,0,1,0,1,1,1,1,0,1,4,0,1,0,1,1,1,1,0,1 },
					{ 1,0,1,0,0,0,0,1,0,1,1,0,1,0,1,0,1,1,0,1 },
					{ 1,0,1,4,1,1,0,0,0,0,1,0,1,0,1,0,0,0,0,1 },
					{ 1,0,1,1,1,1,1,1,1,0,1,0,1,0,1,0,1,1,1,1 },
					{ 1,0,1,0,0,0,0,0,0,0,1,0,1,2,1,0,0,0,0,1 },
					{ 1,0,1,1,1,1,0,1,1,1,1,0,1,1,1,1,0,1,0,5 },
					{ 1,0,1,0,1,0,0,0,0,0,0,0,1,0,1,1,1,1,0,1 },
					{ 1,0,1,0,1,0,1,1,1,1,0,1,1,0,1,0,0,1,0,1 },
					{ 1,0,0,0,1,0,1,0,4,1,0,1,0,0,0,0,1,1,1,1 },
					{ 1,0,1,0,1,1,1,0,1,1,0,1,0,1,1,0,1,1,4,1 },
					{ 1,0,1,0,0,0,0,0,0,1,0,0,0,0,1,0,1,0,0,1 },
					{ 1,0,1,1,1,1,1,1,1,1,1,1,1,0,1,0,1,0,1,1 },
					{ 1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1 },
					{ 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1 } };

int map1[20][30] = { {1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1},
					 {0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,0,0,1,0,0,1,0,0,0,0,0,1},
					 {1,0,1,1,1,1,0,1,1,0,1,0,1,1,1,0,1,2,1,0,1,0,1,1,0,0,0,0,0,1},
					 {1,0,0,0,0,1,0,0,1,0,1,0,1,0,0,0,1,1,1,0,0,0,0,0,0,1,1,1,1,1},
					 {1,1,0,1,0,1,0,1,1,0,1,0,1,0,1,1,0,0,1,0,1,1,1,1,0,1,0,0,4,1},
					 {1,0,0,1,0,1,1,1,1,0,1,0,1,0,1,0,0,1,1,0,1,0,0,0,0,1,0,1,1,1},
					 {1,0,1,0,1,0,0,0,0,0,0,0,1,0,1,0,1,1,0,0,1,0,1,1,0,1,0,0,0,1},
					 {1,0,0,0,1,0,1,0,1,0,1,1,1,0,1,0,0,1,1,0,1,0,0,1,0,1,1,0,1,1},
					 {1,1,1,1,1,0,1,0,1,1,4,0,1,0,1,1,0,0,1,0,1,0,1,1,0,1,0,0,0,1},
					 {1,0,0,0,0,0,1,0,0,0,1,0,1,0,0,0,1,0,1,1,1,0,1,0,0,1,0,1,0,1},
					 {1,0,1,1,1,0,1,0,1,0,0,0,1,1,1,0,0,0,0,0,0,1,0,1,0,1,0,1,0,1},
					 {1,0,1,4,1,0,1,1,1,1,1,1,0,0,1,0,1,1,1,1,0,1,0,1,0,1,0,1,0,1},
					 {1,0,1,0,1,0,0,0,0,0,0,1,0,1,1,0,1,0,0,0,0,1,0,1,0,1,0,1,1,1},
					 {1,0,0,0,0,1,0,1,1,1,0,1,0,1,0,0,1,0,1,1,0,0,0,0,0,1,0,1,0,1},
					 {1,1,1,0,1,0,0,1,0,1,0,1,0,1,1,0,1,0,1,0,1,0,1,1,1,1,0,1,0,1},
					 {1,0,0,0,1,1,1,1,0,1,0,1,0,0,0,0,0,0,0,0,1,4,1,0,0,0,0,1,0,1},
					 {1,0,1,1,0,0,0,1,0,0,0,1,1,1,1,0,1,1,1,0,1,1,1,0,1,1,0,0,0,1},
					 {1,0,0,0,0,1,0,1,1,1,0,0,0,0,0,0,0,0,1,0,0,0,1,0,1,1,0,1,1,1},
					 {1,0,1,0,1,0,0,0,0,0,1,0,1,0,1,0,1,0,1,0,1,0,0,0,1,1,0,0,0,5},
					 {1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1} };

int map2[29][51] = { { 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1 },
{1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1},
{1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 9},
{1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 1},
{1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1},
{1, 0, 1, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 1},
{1, 0, 1, 0, 1, 1, 0, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 0, 1},
{1, 0, 1, 0, 1, 4, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1},
{1, 0, 1, 1, 1, 1, 1, 0, 1, 1, 1, 0, 1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 0, 1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 0, 1},
{1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 4, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 1, 3, 1, 0, 1},
{1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 0, 1, 0, 1, 0, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 0, 1},
{1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1},
{1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 1, 1, 0, 1, 0, 1, 1, 1, 0, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 1, 1, 1, 1},
{1, 0, 1, 0, 0, 0, 1, 0, 1, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 0, 0, 0, 0, 1},
{1, 0, 1, 1, 1, 1, 1, 0, 1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 0, 0, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1},
{1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 1, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 1},
{1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 1, 1, 1, 1, 0, 1, 0, 1, 0, 1, 1, 1, 0, 1},
{1, 0, 1, 4, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 1, 0, 1},
{1, 0, 1, 0, 1, 1, 1, 1, 1, 0, 1, 6, 1, 0, 1, 0, 1, 1, 1, 0, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1},
{1, 0, 1, 0, 0, 0, 0, 0, 1, 0, 1, 2, 1, 0, 1, 0, 1, 0, 1, 0, 0, 0, 1, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1},
{1, 0, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 0, 1, 0, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 0, 1, 0, 1, 1, 1, 0, 1},
{1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 4, 1, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1},
{1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 0, 1, 1, 1, 0, 1, 0, 1, 1, 1, 1, 1, 0, 1, 1, 1},
{1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1},
{1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 1, 1, 0, 1},
{1, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 1, 0, 1, 0, 0, 0, 1},
{1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 0, 1, 0, 1, 0, 1, 0, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
{1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 5},
{1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1} };

int map3[20][20] = { { 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1 },
					{ 1,0,1,1,0,1,1,1,0,0,0,0,0,0,0,1,0,1,1,1 },
					{ 1,0,0,0,0,1,1,1,1,1,1,0,1,0,0,1,0,0,0,1 },
					{ 1,0,1,1,0,1,1,1,1,1,1,1,1,1,0,1,0,0,0,1 },
					{ 1,0,1,1,0,1,1,1,0,0,0,1,0,0,0,1,0,1,0,1 },
					{ 1,0,1,1,0,0,0,0,0,0,0,1,0,1,0,1,0,1,0,1 },
					{ 1,0,0,0,0,1,0,1,1,1,1,1,0,0,0,0,0,1,0,1 },
					{ 1,1,1,1,0,1,0,1,0,0,0,0,0,0,0,0,0,1,0,1 },
					{ 1,0,0,0,0,1,0,1,0,1,0,1,1,1,1,0,0,1,0,1 },
					{ 1,0,0,0,0,1,0,1,0,1,0,0,1,0,0,0,1,1,0,1 },
					{ 1,1,1,1,0,0,1,0,0,1,0,1,1,0,0,0,1,1,0,1 },
					{ 1,1,1,1,0,0,1,0,1,1,0,1,1,0,1,0,1,1,1,1 },
					{ 1,1,1,1,0,1,0,0,0,1,0,1,1,1,0,0,0,0,0,1 },
					{ 1,1,1,0,0,1,0,1,0,1,0,0,1,0,0,0,0,0,0,1 },
					{ 1,1,1,1,0,1,0,0,0,0,0,0,0,0,0,0,1,0,1,1 },
					{ 1,0,1,0,0,1,0,1,0,0,1,0,1,1,1,1,1,0,1,1 },
					{ 1,0,0,0,0,0,0,1,1,1,1,0,0,0,0,0,1,0,1,1 },
					{ 1,0,1,1,1,1,1,1,1,1,1,1,0,0,0,0,1,0,1,1 },
					{ 1,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,1,0,0,5 },
					{ 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1 } };


void gotoxy(int x, int y);   //커서의 위치를 조정하는 함수 선언

void CursorView();   // 커서를 지우거나 크기를 조정하는 함수 선언

void color(int cr); // 색변경 함수

void mapp(); // map출력 함수

void mapp1();

void mapp2();

void mapp3();

void start();

//main문
int main()
{
	CursorView();
	SetConsoleTitle(TEXT("미로 탈출하기!"));// 창이름 변경
	system("mode con cols=70 lines=20");// 창크기 변경
	printf("\n\n\n\n\n");
	printf("\t   _____                                        _    \n");
	printf("\t  |  ___|                                      | |   \n");
	printf("\t  | |__    ___    ___    __ _   _ ___    ___   | |   \n");
	printf("\t  |  __|  / __|  | __|  | _  | |  _  |  / _ |  | |   \n");
	printf("\t  | |___ |__  | | (__  | (_| | | |_) | |  __/  | |   \n");
	printf("\t  |_____| |___/  |___|  |__ _| |  ___|  |___|  |_|   \n");
	printf("\t  시작하려면 Enter!            | |              _     \n");
	printf("\t                               |_|             (_)   \n");
	printf("\n\t   ");
	printf("\n\n\n\n\n");
	printf("\t\t\t\t\t\t\t    Made by vs");
	char l = 'a';
	scanf_s("%c", &l, 1);
	if (l != 0)
	{
		system("cls");
		char a = 0;
		int c = 0; // 별 점수를 저장할 변수
		int co = 10000; // 기본점수
		int x = 2, y = 1;// 플레이어의 초기위치 지정
		int A = 8;
		int B = 6;
		int sk = 0;
		int k = 0; // 열쇠
		int sin = 0;
		int cr = 4;
		int tlqkf = 1;

		printf("\n\n\t\t    0 : 검정    8 : 회색\n");
		printf("\t\t    1 : 파랑    9 : 연한 파랑\n");
		printf("\t\t    2 : 초록   10 : 연한 초록\n");
		printf("\t\t    3 : 옥색   11 : 연한 옥색\n");
		printf("\t\t    4 : 빨강   12 : 연한 빨강\n");
		printf("\t\t    5 : 보라   13 : 연한 보라\n");
		printf("\t\t    6 : 노랑   14 : 연한 노랑\n");
		printf("\t\t    7 : 흰색   15 : 진한 흰색\n\n\n");
		printf("\t\t     좋아하는 색깔을 입력 : ");
		scanf_s("%d", &cr);

		system("cls");
		start(); // 시작 크레딧

		system("mode con cols=40 lines=24");
		mapp();//map출력

		while (1)
		{
			gotoxy(x, y);
			color(cr);
			printf("♥");
			if (_kbhit())
			{
				if (sin == 0)
				{
					if (GetAsyncKeyState(VK_DOWN) & 0x8000 && map[y + 1][x / 2] == 2)
					{
						map[y + 1][x / 2] = 0;
						map[11][19] = 0;
						system("cls");
						mapp();
					}
					if (GetAsyncKeyState(VK_UP) & 0x8000 && map[y - 1][x / 2] == 4)
					{
						map[15][18] = 0;//?:이걸 이용해보자
						gotoxy(x, y--);
						printf("  ");
						gotoxy(x, y);
						printf("♥");
						c++;
					}
					if (GetAsyncKeyState(VK_UP) & 0x8000 && map[y - 1][x / 2] == 0)
					{
						gotoxy(x, y--);
						printf("  ");
						gotoxy(x, y);
						printf("♥");
						co -= 5;
					}
					if (GetAsyncKeyState(VK_DOWN) & 0x8000 && map[y + 1][x / 2] == 4)
					{
						map[8][3] = 0;
						gotoxy(x, y++);
						printf("  ");
						gotoxy(x, y);
						printf("♥");
						c++;
					}
					if (GetAsyncKeyState(VK_DOWN) & 0x8000 && map[y + 1][x / 2] == 0)
					{
						gotoxy(x, y++);
						printf("  ");
						gotoxy(x, y);
						printf("♥");
						co -= 5;
					}
					if (GetAsyncKeyState(VK_RIGHT) & 0x8000 && map[y][x / 2 + 1] == 4)
					{
						map[14][8] = 0;
						gotoxy(x++, y);
						printf("  ");
						gotoxy(++x, y);
						printf("♥");
						c++;
					}
					if (GetAsyncKeyState(VK_RIGHT) & 0x8000 && map[y][x / 2 + 1] == 0)
					{
						gotoxy(x++, y);
						printf("  ");
						gotoxy(++x, y);
						printf("♥");
						co += 5;
					}
					if (GetAsyncKeyState(VK_LEFT) & 0x8000 && map[y][x / 2 - 1] == 4)
					{
						map[6][10] = 0;
						gotoxy(x--, y);
						printf("  ");
						gotoxy(--x, y);
						printf("♥");
						c++;
					}
					if (GetAsyncKeyState(VK_LEFT) & 0x8000 && map[y][x / 2 - 1] == 0)
					{
						gotoxy(x--, y);
						printf("  ");
						gotoxy(--x, y);
						printf("♥");
						co -= 5;
					}
					if (x == 38 && y == 11)
					{
						sin = 1;
						x = 2;
						y = 1;
						gotoxy(x, y);
						system("cls");
						system("mode con cols=70 lines=20");
						printf("\n\n\n\n\n\n\n");
						color(12);
						printf("\t\t\t     1");
						Sleep(200);
						printf("단");
						Sleep(200);
						printf("계");
						Sleep(200);
						printf(" ");
						Sleep(200);
						printf("완");
						Sleep(200);
						printf("료");
						Sleep(200);
						printf("!");
						Sleep(200);
						system("cls");
						system("mode con cols=60 lines=24");
						mapp1();
					}
				}
				else if (sin == 1)
				{
					if (GetAsyncKeyState(VK_DOWN) & 0x8000 && map1[y + 1][x / 2] == 2)
					{
						map1[2][17] = 0;
						map1[18][29] = 0;
						system("cls");
						mapp1();
					}
					if (GetAsyncKeyState(VK_UP) & 0x8000 && map1[y - 1][x / 2] == 4)
					{
						map1[11][3] = 0;//?:이걸 이용해보자
						gotoxy(x, y--);
						printf("  ");
						gotoxy(x, y);
						printf("♥");
						c++;
					}
					if (GetAsyncKeyState(VK_UP) & 0x8000 && map1[y - 1][x / 2] == 0)
					{
						gotoxy(x, y--);
						printf("  ");
						gotoxy(x, y);
						printf("♥");
						co -= 5;
					}
					if (GetAsyncKeyState(VK_DOWN) & 0x8000 && map1[y + 1][x / 2] == 4)
					{
						map1[15][21] = 0;
						gotoxy(x, y++);
						printf("  ");
						gotoxy(x, y);
						printf("♥");
						c++;
					}
					if (GetAsyncKeyState(VK_DOWN) & 0x8000 && map1[y + 1][x / 2] == 0)
					{
						gotoxy(x, y++);
						printf("  ");
						gotoxy(x, y);
						printf("♥");
						co -= 5;
					}
					if (GetAsyncKeyState(VK_RIGHT) & 0x8000 && map1[y][x / 2 + 1] == 4)
					{
						map1[4][28] = 0;
						gotoxy(x++, y);
						printf("  ");
						gotoxy(++x, y);
						printf("♥");
						c++;
					}
					if (GetAsyncKeyState(VK_RIGHT) & 0x8000 && map1[y][x / 2 + 1] == 0)
					{
						gotoxy(x++, y);
						printf("  ");
						gotoxy(++x, y);
						printf("♥");
						co += 5;
					}
					if (GetAsyncKeyState(VK_LEFT) & 0x8000 && map1[y][x / 2 - 1] == 4)
					{
						map1[8][10] = 0;
						gotoxy(x--, y);
						printf("  ");
						gotoxy(--x, y);
						printf("♥");
						c++;
					}
					if (GetAsyncKeyState(VK_LEFT) & 0x8000 && map1[y][x / 2 - 1] == 0)
					{
						gotoxy(x--, y);
						printf("  ");
						gotoxy(--x, y);
						printf("♥");
						co -= 5;
					}
					if (x == 58 && y == 18)
					{
						sin = 2;
						x = 2;
						y = 1;
						system("cls");
						system("mode con cols=70 lines=20");
						printf("\n\n\n\n\n\n\n\n");
						color(12);
						printf("\t\t\t     2");
						Sleep(200);
						printf("단");
						Sleep(200);
						printf("계");
						Sleep(200);
						printf(" ");
						Sleep(200);
						printf("완");
						Sleep(200);
						printf("료");
						Sleep(200);
						printf("!");
						Sleep(200);
						system("cls");

						printf("\n\n\n\n\n\n\n\n");
						printf("\t\t     참");
						Sleep(200);
						printf("고");
						Sleep(200);
						printf("로");
						Sleep(200);
						printf(" ");
						Sleep(200);
						printf("▒▒");
						Sleep(200);
						printf("이");
						Sleep(200);
						printf("거");
						printf(" ");
						Sleep(200);
						Sleep(200);
						printf("다");
						Sleep(200);
						printf("으");
						Sleep(200);
						printf("면");
						printf(" ");
						Sleep(200);
						Sleep(200);
						printf("주");
						Sleep(200);
						printf("금");
						Sleep(200);
						printf("!");
						Sleep(200);
					tlqkf:
						x = 2;
						y = 1;
						system("mode con cols=102 lines=37");
						mapp2();

						if (sin == 2)
						{
							color(cr);
							while (1)
							{
								if (GetAsyncKeyState(VK_UP) & 0x8000 && map2[y - 1][x / 2] == 3)// 전화
								{
									map2[18][11] = 0;
									map2[9][47] = 0;
									system("cls");
									mapp2();
									color(cr);
								}
								if (GetAsyncKeyState(VK_DOWN) & 0x8000 && map2[y + 1][x / 2] == 6)
								{
									system("mode con cols=70 lines=20");
									system("cls");
									color(9);
									printf("\n\n\n\n\n");
									printf("      □■□■□■□■□■□■□■□■□■□■□■□■□■□■□\n");
									Sleep(200);
									printf("      ■□□□□□□□□□□□□□□□□□□□□□□□□□□□■\n");
									Sleep(200);
									printf("      □□□□□□□□■■■□□□■□□■■■■□□□□□□□□\n");
									Sleep(200);
									printf("      ■□□□□□□□■□□■□□□□□■□□□□□□□□□□■\n");
									Sleep(200);
									printf("      □□□□□□□□■□□■□□■□□■■■■□□□□□□□□\n");
									Sleep(200);
									printf("      ■□□□□□□□■□□■□□■□□■□□□□□□□□□□■\n");
									Sleep(200);
									printf("      □□□□□□□□■■■□□□■□□■■■■□□□□□□□□\n");
									Sleep(200);
									printf("      ■□□□□□□□□□□□□□□□□□□□□□□□□□□□■\n");
									Sleep(200);
									printf("      □■□■□■□■□■□■□■□■□■□■□■□■□■□■□\n");
									Sleep(200);
									break;
								}
								if (GetAsyncKeyState(VK_DOWN) & 0x8000 && map2[y + 1][x / 2] == 2)
								{
									map2[27][50] = 0;
									map2[19][11] = 0;
									system("cls");
									mapp2();
									color(cr);
								}
								if (GetAsyncKeyState(VK_UP) & 0x8000 && map2[y - 1][x / 2] == 6)
								{
									system("mode con cols=70 lines=20");
									system("cls");
									color(9);
									printf("\n\n\n\n\n");
									printf("      □■□■□■□■□■□■□■□■□■□■□■□■□■□■□\n");
									Sleep(200);
									printf("      ■□□□□□□□□□□□□□□□□□□□□□□□□□□□■\n");
									Sleep(200);
									printf("      □□□□□□□□■■■□□□■□□■■■■□□□□□□□□\n");
									Sleep(200);
									printf("      ■□□□□□□□■□□■□□□□□■□□□□□□□□□□■\n");
									Sleep(200);
									printf("      □□□□□□□□■□□■□□■□□■■■■□□□□□□□□\n");
									Sleep(200);
									printf("      ■□□□□□□□■□□■□□■□□■□□□□□□□□□□■\n");
									Sleep(200);
									printf("      □□□□□□□□■■■□□□■□□■■■■□□□□□□□□\n");
									Sleep(200);
									printf("      ■□□□□□□□□□□□□□□□□□□□□□□□□□□□■\n");
									Sleep(200);
									printf("      □■□■□■□■□■□■□■□■□■□■□■□■□■□■□\n");
									Sleep(200);
									break;
								}
								if (GetAsyncKeyState(VK_UP) & 0x8000 && map2[y - 1][x / 2] == 4)
								{
									map2[17][3] = 0;
									gotoxy(x, y--);
									printf("  ");
									gotoxy(x, y);
									printf("♥");
									c++;
								}
								if (GetAsyncKeyState(VK_UP) & 0x8000 && map2[y - 1][x / 2] == 0)
								{
									gotoxy(x, y--);
									printf("  ");
									gotoxy(x, y);
									printf("♥");
									co -= 5;
								}
								if (GetAsyncKeyState(VK_DOWN) & 0x8000 && map2[y + 1][x / 2] == 4)
								{
									map2[21][37] = 0;
									gotoxy(x, y++);
									printf("  ");
									gotoxy(x, y);
									printf("♥");
									c++;
								}
								if (GetAsyncKeyState(VK_DOWN) & 0x8000 && map2[y + 1][x / 2] == 0)
								{
									gotoxy(x, y++);
									printf("  ");
									gotoxy(x, y);
									printf("♥");
									co -= 5;
								}
								if (GetAsyncKeyState(VK_RIGHT) & 0x8000 && map2[y][x / 2 + 1] == 9)
								{
									map2[y][x / 2 + 1] = 1;
									x = 2, y = 1;
									map2[2][49] == 0;
									system("cls");
									mapp2();
									system("mode con cols=70 lines=20");
									printf("\n\n\n\n\n\n\n\n");
									printf("\t\t\t     히");
									Sleep(200);
									printf("든");
									Sleep(200);
									printf(" ");
									Sleep(200);
									printf("스");
									Sleep(200);
									printf("테");
									Sleep(200);
									printf("이");
									Sleep(200);
									printf("지");
									Sleep(200);
									printf("!");
									Sleep(200);
									system("cls");
									system("mode con cols=40 lines=24");
									mapp3();
									co += 1000;
									while (1)
									{
										if (GetAsyncKeyState(VK_UP) & 0x8000 && map3[y - 1][x / 2] == 0)
										{
											gotoxy(x, y--);
											printf("  ");
											gotoxy(x, y);
											printf("♥");
											co -= 5;
										}
										if (GetAsyncKeyState(VK_DOWN) & 0x8000 && map3[y + 1][x / 2] == 0)
										{
											gotoxy(x, y++);
											printf("  ");
											gotoxy(x, y);
											printf("♥");
											co -= 5;
										}
										if (GetAsyncKeyState(VK_RIGHT) & 0x8000 && map3[y][x / 2 + 1] == 0)
										{
											gotoxy(x++, y);
											printf("  ");
											gotoxy(++x, y);
											printf("♥");
											co += 5;
										}
										if (GetAsyncKeyState(VK_RIGHT) & 0x8000 && map3[y][x / 2 + 1] == 5)
										{
											map3[18][19] = 0;
											system("cls");
											mapp3();
										}
										if (GetAsyncKeyState(VK_LEFT) & 0x8000 && map3[y][x / 2 - 1] == 0)
										{
											gotoxy(x--, y);
											printf("  ");
											gotoxy(--x, y);
											printf("♥");
											co -= 5;
										}
										if (x == 38 && y == 18)
										{
											system("mode con cols=70 lines=20");
											printf("\n\n\n\n\n\n\n\n");
											printf("\t\t\t히");
											Sleep(200);
											printf("든");
											Sleep(200);
											printf(" ");
											Sleep(200);
											printf("스");
											Sleep(200);
											printf("테");
											Sleep(200);
											printf("이");
											Sleep(200);
											printf("지");
											Sleep(200);
											printf("clear");
											Sleep(200);
											system("cls");
											goto tlqkf;
										}
										Sleep(150);
									}
								}
								if (GetAsyncKeyState(VK_RIGHT) & 0x8000 && map2[y][x / 2 + 1] == 4)
								{
									map2[9][31] = 0;
									gotoxy(x++, y);
									printf("  ");
									gotoxy(++x, y);
									printf("♥");
									c++;
								}
								if (GetAsyncKeyState(VK_RIGHT) & 0x8000 && map2[y][x / 2 + 1] == 0)
								{
									gotoxy(x++, y);
									printf("  ");
									gotoxy(++x, y);
									printf("♥");
									co += 5;
								}
								if (GetAsyncKeyState(VK_LEFT) & 0x8000 && map2[y][x / 2 - 1] == 4)
								{
									map2[7][5] = 0;
									gotoxy(x--, y);
									printf("  ");
									gotoxy(--x, y);
									printf("♥");
									c++;
								}
								if (GetAsyncKeyState(VK_LEFT) & 0x8000 && map2[y][x / 2 - 1] == 0)
								{
									gotoxy(x--, y);
									printf("  ");
									gotoxy(--x, y);
									printf("♥");
									co -= 5;
								}
								if (x == 98 && y == 26)
								{
									x = 2;
									y = 1;
									gotoxy(x, y);
									system("cls");
									system("mode con cols=70 lines=20");
									printf("\n\n\n\n\n\n\n\n");
									color(12);
									printf("\t\t\t     3");
									Sleep(200);
									printf("단");
									Sleep(200);
									printf("계");
									Sleep(200);
									printf(" ");
									Sleep(200);
									printf("완");
									Sleep(200);
									printf("료");
									Sleep(200);
									printf("!");
									Sleep(200);
									system("cls");
									Sleep(400);
									printf("\n\n\n\n\n");
									printf("     □■□■□■□■□■□■□■□■□■□■□■□■□■□■□\n");
									Sleep(200);
									printf("     ■□□□□□□□□□□□□□□□□□□□□□□□□□□□■\n");
									Sleep(200);
									printf("     □□□□□□■■■□□■■□■■□□■□□■■■□□□□□\n");
									Sleep(200);
									printf("     ■□□□□□■□□□□□■■■□□□□□□□■□□□□□■\n");
									Sleep(200);
									printf("     □□□□□□■■■□□□□■□□□□■□□□■□□□□□□\n");
									Sleep(200);
									printf("     ■□□□□□■□□□□□■■■□□□■□□□■□□□□□■\n");
									Sleep(200);
									printf("     □□□□□□■■■□□■■□■■□□■□□□■□□□□□□\n");
									Sleep(200);
									printf("     ■□□□□□□□□□□□□□□□□□□□□□□□□□□□■\n");
									Sleep(200);
									printf("     □■□■□■□■□■□■□■□■□■□■□■□■□■□■□\n");
									Sleep(200);
									printf("\n  ---------------------------<%d>-------------------------------\n", (c * 80) + co);
									Sleep(200);
									break;
								}
								Sleep(150);
							}
						}
					}
				}
				Sleep(150);
			}
		}
	}
	return 0;
}

// 시작 함수
void start()
{
	if (_kbhit())
	{
		return 0;
	}
	printf("\t 이 ");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("게임");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("은");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf(" 공");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("간");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("지");
	if (_kbhit())
	{
		return 0;
	}
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("각");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("능");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("력");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf(" 향");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("상");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("을");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf(" 위");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("하");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("여");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf(" 제");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("작");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("되");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("었");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("습");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("니");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("다.");
	Sleep(500);
	if (_kbhit())
	{
		return 0;
	}

	printf("\n\n");
	printf("\t\t\t 이");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("동");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("은");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf(" 방");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("향");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("키");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("입");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("니");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("다.");

	printf("\n\n");
	printf("\t\t  로");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("딩");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("이");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf(" 끝");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("나");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("면");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf(" 게");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("임");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("이");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf(" 시");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("작");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("됩");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("니");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}
	printf("다.");
	Sleep(200);
	if (_kbhit())
	{
		return 0;
	}

	printf("\n\n\n");
	color(4);
	printf("\t\t         ■■          ■■");
	Sleep(200);
	printf("\n\t\t       ■■■■      ■■■■");
	Sleep(200);
	color(6);
	printf("\n\t\t     ■■■■■■■■■■■■■");
	Sleep(200);
	printf("\n\t\t   ■■■■■■■■■■■■■■■");
	Sleep(200);
	color(2);
	printf("\n\t\t   ■■■■■■■■■■■■■■■");
	Sleep(200);
	printf("\n\t\t     ■■■■■■■■■■■■■");
	Sleep(200);
	color(9);
	printf("\n\t\t       ■■■■■■■■■■■");
	Sleep(200);
	printf("\n\t\t         ■■■■■■■■■");
	Sleep(200);
	color(1);
	printf("\n\t\t           ■■■■■■■");
	Sleep(200);
	printf("\n\t\t             ■■■■■");
	Sleep(200);
	color(5);
	printf("\n\t\t               ■■■");
	Sleep(200);
	printf("\n\t\t                 ■");
	Sleep(1000);
}

// map출력 함수
void mapp()
{
	for (int i = 0; i < 20; i++)
	{
		for (int k = 0; k < 20; k++)
		{
			if (map[i][k] == 1)
			{
				color(8);
				printf("■");
			}
			if (map[i][k] == 0)
			{
				printf("　");
			}
			if (map[i][k] == 2)
			{
				printf("키");
			}
			if (map[i][k] == 3)
			{
				printf("→");
			}
			if (map[i][k] == 4)
			{
				color(6);
				printf("★");
			}
			if (map[i][k] == 5)
			{
				color(11);
				printf("▥");
			}
		}
		printf("\n");
	}
	color(15);
	printf("\n");
	printf("========================================\n");
	printf("점수 : ★      열쇠 : 키       출구 : ▥");
}

void mapp1()
{
	for (int i = 0; i < 20; i++)
	{
		for (int k = 0; k < 30; k++)
		{
			if (map1[i][k] == 1)
			{
				color(8);
				printf("■");
			}
			if (map1[i][k] == 0)
			{
				printf("　");
			}
			if (map1[i][k] == 2)
			{
				printf("키");
			}
			if (map1[i][k] == 3)
			{
				printf("→");
			}
			if (map1[i][k] == 4)
			{
				color(6);
				printf("★");
			}
			if (map1[i][k] == 5)
			{
				color(11);
				printf("▥");
			}
		}
		printf("\n");
	}
	color(15);
	printf("\n");
	printf("============================================================\n");
	printf("점수 : ★                열쇠 : 키                 출구 : ▥");
}

void mapp2()
{
	for (int i = 0; i < 29; i++)
	{
		for (int k = 0; k < 51; k++)
		{
			if (map2[i][k] == 1)
			{
				color(8);
				printf("■");
			}
			if (map2[i][k] == 0)
			{
				printf("　");
			}
			if (map2[i][k] == 2)
			{
				printf("키");
			}
			if (map2[i][k] == 3)
			{
				color(13);
				printf("☎");
			}
			if (map2[i][k] == 4)
			{
				color(6);
				printf("★");
			}
			if (map2[i][k] == 5)
			{
				color(11);
				printf("▥");
			}
			if (map2[i][k] == 6)
			{
				color(2);
				printf("▒▒");
			}
			if (map2[i][k] == 9)
			{
				color(7);
				printf("▩");
			}
		}
		printf("\n");
	}
	color(15);
	printf("\n");
	printf("======================================================================================================\n");
	printf(" 점수 : ★             함정 : ▒▒              전화 : ☎              열쇠 : 키             출구 : ▥ ");
}

void mapp3()
{
	for (int i = 0; i < 20; i++)
	{
		for (int k = 0; k < 20; k++)
		{
			if (map3[i][k] == 1)
			{
				color(0);
				printf("■");
			}
			if (map3[i][k] == 0)
			{
				printf("　");
			}
			if (map3[i][k] == 5)
			{
				color(0);
				printf("♨");
			}
		}
		printf("\n");
	}
	color(15);
	printf("\n");
	printf("========================================\n");
	printf("             Invisible Mode             ");
}

// 좌표변경 함수 
void gotoxy(int x, int y)
{
	COORD pos = { x,y };
	SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE), pos);
}

//색 변경함수
void color(int cr)
{
	SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), cr);
}

// 커서변경 함수
void CursorView()
{
	CONSOLE_CURSOR_INFO cursorInfo = { 0, };
	cursorInfo.dwSize = 1;
	cursorInfo.bVisible = FALSE;
	SetConsoleCursorInfo(GetStdHandle(STD_OUTPUT_HANDLE), &cursorInfo);
}
