---
title: Przykładowy program więlowątkowy w języku C
ms.date: 08/09/2019
ms.assetid: 4706f6cd-ff9c-4dbf-99a2-1c999b568f17
ms.openlocfilehash: eb1a07558dd9446e167c27ad08891f88c37fb4ec
ms.sourcegitcommit: b3d19b5f59f3a5d90c24f9f16c73bad4c5eb6944
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71195816"
---
# <a name="sample-multithread-c-program"></a>Przykładowy program więlowątkowy w języku C

Odbicie. c jest przykładowym programem wielowątkowej, który tworzy nowy wątek każdorazowo po wpisaniu `a` litery `A` lub. Każdy wątek odbija literę innego koloru wokół ekranu. Można utworzyć maksymalnie 32 wątków. Normalne zakończenie programu ma miejsce, gdy `q` lub `Q` jest wpisane.

## <a name="compile-and-link-a-multithread-program"></a>Kompiluj i łącz program wielowątkowej

Programy są domyślnie kompilowane jako wielowątkowe.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>Aby skompilować i połączyć program wielowątkowej. c z poziomu środowiska deweloperskiego

::: moniker range=">=vs-2019"

1. W menu **plik** wybierz pozycję **Nowy** > **projekt**.

1. W oknie dialogowym **Tworzenie nowego projektu** wybierz szablon **aplikacji konsoli** , który zawiera **C++** znaczniki **systemu Windows**i **konsoli** . Wybierz pozycję **dalej** , aby kontynuować.

1. W oknie dialogowym **Konfigurowanie nowego projektu** wprowadź nazwę projektu, na przykład "odbijanie". Wybierz pozycję **Utwórz** , aby kontynuować.

1. W oknie **Eksplorator rozwiązań** Otwórz folder **pliki źródłowe** w ramach projektu, a następnie zmień nazwę pliku źródłowego, aby miał rozszerzenie. c.

1. W oknie Edycja usuń istniejący kod źródłowy i zastąp go kodem przykładowym.

1. W menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

1. Naciśnij klawisz **F5** , aby uruchomić program w debugerze.

::: moniker-end

::: moniker range="<=vs-2017"

1. W menu **plik** wybierz pozycję **Nowy** > **projekt**.

1. W oknie dialogowym **Nowy projekt** wybierz pozycję **Wizualizacja C++**  w okienku po lewej stronie, a następnie w środkowym okienku wybierz pozycję **pusty projekt** .

1. W polu **Nazwa** wprowadź nazwę projektu, na przykład "odbijanie". Wybierz **przycisk OK** , aby utworzyć pusty projekt.

1. W oknie **Eksplorator rozwiązań** Otwórz folder **pliki źródłowe** w ramach projektu i Dodaj do projektu plik zawierający kod źródłowy języka C.

1. W menu **kompilacja** Skompiluj projekt, wybierając polecenie **Kompiluj rozwiązanie** .

1. Naciśnij klawisz **F5** , aby uruchomić program w debugerze.

::: moniker-end

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>Aby skompilować i połączyć program wielowątkowej. c z wiersza polecenia

1. Kompiluj i Połącz program:

    ```cmd
    cl bounce.c
    ```

## <a name="example"></a>Przykład

Aby skompilować w wierszu polecenia, skopiuj i Zapisz ten przykład w pliku źródłowym z rozszerzeniem. c. W środowisku IDE Zastąp każdy kod źródłowy utworzony przez szablon tym przykładem:

```C
// sample_multithread_c_program.c
// compile with: /c
//
//  Bounce - Creates a new thread each time the letter 'a' is typed.
//  Each thread bounces a character of a different color around
//  the screen. All threads are terminated when the letter 'Q' is
//  entered.
//

#include <windows.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>
#include <conio.h>
#include <process.h>

#define MAX_THREADS  32

// The function getrandom returns a random number between
// min and max, which must be in integer range.
#define getrandom( min, max ) (SHORT)((rand() % (int)(((max) + 1) - \
                               (min))) + (min))

int main(void);                    // Thread 1: main
void KbdFunc(void);                // Keyboard input, thread dispatch
void BounceProc(void* MyID);       // Threads 2 to n: display
void ClearScreen(void);            // Screen clear
void ShutDown(void);               // Program shutdown
void WriteTitle(int ThreadNum);    // Display title bar information

HANDLE  hConsoleOut;                 // Handle to the console
HANDLE  hRunMutex;                   // "Keep Running" mutex
HANDLE  hScreenMutex;                // "Screen update" mutex
int     ThreadNr;                    // Number of threads started
CONSOLE_SCREEN_BUFFER_INFO csbiInfo; // Console information
COORD   consoleSize;
BOOL    bTrails;

int main() // Thread One
{
    // Get display screen information & clear the screen.
    hConsoleOut = GetStdHandle(STD_OUTPUT_HANDLE);
    GetConsoleScreenBufferInfo(hConsoleOut, &csbiInfo);
    consoleSize.X = csbiInfo.srWindow.Right;
    consoleSize.Y = csbiInfo.srWindow.Bottom;
    ClearScreen();
    WriteTitle(0);

    // Create the mutexes and reset thread count.
    hScreenMutex = CreateMutexW(NULL, FALSE, NULL);  // Cleared
    hRunMutex = CreateMutexW(NULL, TRUE, NULL);      // Set
    ThreadNr = 0;
    bTrails = FALSE;

    // Start waiting for keyboard input to dispatch threads or exit.
    KbdFunc();

    // All threads done. Clean up handles.
    if (hScreenMutex) CloseHandle(hScreenMutex);
    if (hRunMutex) CloseHandle(hRunMutex);
    if (hConsoleOut) CloseHandle(hConsoleOut);
}

void ShutDown(void) // Shut down threads
{
    while (ThreadNr > 0)
    {
        // Tell thread to die and record its death.
        ReleaseMutex(hRunMutex);
        ThreadNr--;
    }

    // Clean up display when done
    WaitForSingleObject(hScreenMutex, INFINITE);
    ClearScreen();
}

void KbdFunc(void) // Dispatch and count threads.
{
    int         KeyInfo;

    do
    {
        KeyInfo = _getch();
        if (tolower(KeyInfo) == 'a' &&
            ThreadNr < MAX_THREADS)
        {
            ThreadNr++;
            _beginthread(BounceProc, 0, &ThreadNr);
            WriteTitle(ThreadNr);
        }
        if (tolower(KeyInfo) == 't')
        {
            bTrails = !bTrails;
        }
    } while (tolower(KeyInfo) != 'q');

    ShutDown();
}

void BounceProc(void* pMyID)
{
    wchar_t MyCell, OldCell;
    WORD    MyAttrib, OldAttrib = 0;
    wchar_t BlankCell = 0x20;
    COORD   Coords, Delta;
    COORD   Old = { 0,0 };
    DWORD   Dummy;
    char* MyID = (char*)pMyID;

    // Generate update increments and initial
    // display coordinates.
    srand((unsigned int)* MyID * 3);

    Coords.X = getrandom(0, consoleSize.X - 1);
    Coords.Y = getrandom(0, consoleSize.Y - 1);
    Delta.X = getrandom(-3, 3);
    Delta.Y = getrandom(-3, 3);

    // Set up character & generate color
    // attribute from thread number.
    if (*MyID > 16)
        MyCell = 0x60 + *MyID - 16; // lower case
    else
        MyCell = 0x40 + *MyID;      // upper case
    MyAttrib = *MyID & 0x0f;   // force black background

    do
    {
        // Wait for display to be available, then lock it.
        WaitForSingleObject(hScreenMutex, INFINITE);

        if (!bTrails)
        {
            // If we still occupy the old screen position, blank it out.
            ReadConsoleOutputCharacterW(hConsoleOut, &OldCell, 1,
                Old, &Dummy);
            ReadConsoleOutputAttribute(hConsoleOut, &OldAttrib, 1,
                Old, &Dummy);
            if ((OldCell == MyCell) && (OldAttrib == MyAttrib))
                WriteConsoleOutputCharacterW(hConsoleOut, &BlankCell, 1,
                    Old, &Dummy);
        }

        // Draw new character, then clear screen lock
        WriteConsoleOutputCharacterW(hConsoleOut, &MyCell, 1,
            Coords, &Dummy);
        WriteConsoleOutputAttribute(hConsoleOut, &MyAttrib, 1,
            Coords, &Dummy);
        ReleaseMutex(hScreenMutex);

        // Increment the coordinates for next placement of the block.
        Old.X = Coords.X;
        Old.Y = Coords.Y;
        Coords.X += Delta.X;
        Coords.Y += Delta.Y;

        // If we are about to go off the screen, reverse direction
        if (Coords.X < 0 || Coords.X >= consoleSize.X)
        {
            Delta.X = -Delta.X;
            Beep(400, 50);
        }
        if (Coords.Y < 0 || Coords.Y > consoleSize.Y)
        {
            Delta.Y = -Delta.Y;
            Beep(600, 50);
        }
    }
    // Repeat while RunMutex is still taken.
    while (WaitForSingleObject(hRunMutex, 75L) == WAIT_TIMEOUT);
}

void WriteTitle(int ThreadNum)
{
    enum
    {
        sizeOfNThreadMsg = 120
    };
    wchar_t    NThreadMsg[sizeOfNThreadMsg] = { L"" };

    swprintf_s(NThreadMsg, sizeOfNThreadMsg,
        L"Threads running: %02d.  Press 'A' "
        L"to start a thread, 'T' to toggle "
        L"trails, 'Q' to quit.", ThreadNum);
    SetConsoleTitleW(NThreadMsg);
}

void ClearScreen(void)
{
    DWORD    dummy = 0;
    COORD    Home = { 0, 0 };
    FillConsoleOutputCharacterW(hConsoleOut, L' ',
        consoleSize.X * consoleSize.Y,
        Home, &dummy);
}
```

## <a name="see-also"></a>Zobacz także

[Wielowątkowość z językiem C i podsystemem Win32](multithreading-with-c-and-win32.md)
