@@ -1,9 +1,13 @@
#include <iostream>
#include <fstream>
#include <string>
#include <windows.h>
#include <stdio.h>

HANDLE hStdin;
DWORD fdwSaveOldMode;
int score = 0;
std::string Name;

VOID ErrorExit(LPSTR);
VOID KeyEventProc(KEY_EVENT_RECORD);
@@ -12,6 +16,18 @@ VOID ResizeEventProc(WINDOW_BUFFER_SIZE_RECORD);

int main(VOID)
{
	std::cout << "                  eeeeeee   l       ccccccc  ooooooo                   eeeeeee " << std::endl;
	std::cout << " w              w e         l       c        o     o      m     m      e       " << std::endl;
	std::cout << "  w     ww     w  e         l       c        o     o     m m   m m     e       " << std::endl;
	std::cout << "   w   w  w   w   eeeee     l       c        o     o    m   m m   m    eeeee   " << std::endl;
	std::cout << "    w w    w w    e         l       c        o     o   m     m     m   e       " << std::endl;
	std::cout << "     w      w     eeeeeee   llllll  ccccccc  ooooooo  m             m  eeeeeee " << std::endl;
	std::cout << "===============================================================================" << std::endl;
	std::cout << "Enter Your Name " << std::endl;
	std::cin >> Name;
	std::cout << "hit e whenever you would like to quit" << std::endl;


	DWORD cNumRead, fdwMode, i;
	INPUT_RECORD irInBuf[128];
	int counter = 0;
@@ -38,7 +54,7 @@ int main(VOID)
	while (true)
	{
		// Wait for the events. 

		
		if (!ReadConsoleInput(
			hStdin,      // input buffer handle 
			irInBuf,     // buffer to read into 
@@ -79,6 +95,9 @@ int main(VOID)

	SetConsoleMode(hStdin, fdwSaveOldMode);




	return 0;
}

@@ -92,24 +111,178 @@ VOID ErrorExit(LPSTR lpszMessage)

	ExitProcess(0);
}
void ColorPicker(int color)
{
	SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), color);
}

void outputs()
{

	if (score == 10)
	{
		std::cout << "Welp ya gotta start somewhere" << std::endl;
	}
	else if (score == 12)
	{
		std::cout << "Hey my favorite number :D" << std::endl;
	}
	else if (score == 18)
	{
		std::cout << "Congrats your legal now" << std::endl;
	}
	else if (score == 21)
	{
		std::cout << "yay alchohol" << std::endl;
	}
	else if (score == 30)
	{
		std::cout << "there goes your hair" << std::endl;
	}
	else if (score == 42)
	{
		std::cout << "the answer to all" << std::endl;
	}
	else if (score == 69)
	{
		std::cout << "hehehehe" << std::endl;
	}
	else if (score == 88)
	{
		std::cout << "four circles" << std::endl;
	}
	else if (score == 99)
	{
		std::cout << "So close" << std::endl;
	}
	else if (score == 100)
	{
		std::cout << "there you go" << std::endl;
	}
	else if (score == 112)
	{
		std::cout << "its a bigger 12" << std::endl;
	}
	else if (score == 180)
	{
		std::cout << "Half way jk lol" << std::endl;
	}
	else if (score == 360)
	{
		std::cout << " fuckin no scoped bitch" << std::endl;
	}
	else if (score == 404)
	{
		std::cout << "ERROR 'System32' DELETED" << std::endl;
	}
	else if (score == 420)
	{
		std::cout << " what did u expect a weed joke you drugy" << std::endl;
	}
	else if (score == 500)
	{
		std::cout << "noice" << std::endl;
	}
	else if (score == 666)
	{
		std::cout << "SATAN!!!" << std::endl;
	}
	else if (score == 720)
	{
		std::cout << " double 360 no scope nerd!!" << std::endl;
	}
	else if (score == 314)
	{
		std::cout << "NERD!!!!" << std::endl;
	}
	else if (score == 999)
	{
		std::cout << "1 1/2 evil!!" << std::endl;
	}
	else if (score == 333)
	{
		std::cout << " 1/2 evil" << std::endl;
	}
}

VOID KeyEventProc(KEY_EVENT_RECORD ker)
{
	//printf("Key event: ");
	
	
	if (ker.wVirtualKeyCode == VK_SPACE)


	if (ker.wVirtualKeyCode == VK_SPACE && ker.bKeyDown == false)
	{
		int score = 0;

		score++;
		printf("Mash that button!!\n");



		if (score <= 1000000)
		{
			ColorPicker(28);
		}
		if (score <= 100000)
		{
			ColorPicker(12);
		}
		if (score <= 10000)
		{
			ColorPicker(13);
		}
		if (score <= 1000)
		{
			ColorPicker(14);
		}
		if (score <= 100)
		{
			ColorPicker(11);
		}
		if (score <= 10)
		{
			ColorPicker(10);
		}

		outputs();

		std::cout << score << std::endl;
	}

	return;
	if (ker.bKeyDown)
		printf("key pressed\n");
	else printf("key released\n");

	else if (ker.uChar.AsciiChar == 'e' && ker.bKeyDown == false)
	{

		std::string Entry;

		std::fstream file;
		file.open("High Scores.txt");
		if (file.fail())
		{
			std::cerr << "Scores not found" << std::endl;
		}



		std::string buffer;
		while (std::getline(file, buffer))
		{

			std::cout << buffer << std::endl;
		}

		file.clear();
		file.seekp(0, std::ios_base::end);


		file << std::endl << Name<< ": " << score;

		file.flush();

		system("pause");
		file.close();
		exit(0);

	}
}

VOID MouseEventProc(MOUSE_EVENT_RECORD mer)
