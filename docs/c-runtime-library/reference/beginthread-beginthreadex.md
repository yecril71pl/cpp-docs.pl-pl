---
title: _beginthread, _beginthreadex
ms.date: 02/27/2018
api_name:
- _beginthread
- _beginthreadex
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- beginthread
- _beginthread
- beginthreadex
- _beginthreadex
helpviewer_keywords:
- _beginthread function
- threading [C++], creating threads
- beginthreadex function
- _beginthreadex function
- beginthread function
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
ms.openlocfilehash: 8714e945464dd98483f9347c4226321a96cda61c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943631"
---
# <a name="_beginthread-_beginthreadex"></a>_beginthread, _beginthreadex

Tworzy wątek.

## <a name="syntax"></a>Składnia

```cpp
uintptr_t _beginthread( // NATIVE CODE
   void( __cdecl *start_address )( void * ),
   unsigned stack_size,
   void *arglist
);
uintptr_t _beginthread( // MANAGED CODE
   void( __clrcall *start_address )( void * ),
   unsigned stack_size,
   void *arglist
);
uintptr_t _beginthreadex( // NATIVE CODE
   void *security,
   unsigned stack_size,
   unsigned ( __stdcall *start_address )( void * ),
   void *arglist,
   unsigned initflag,
   unsigned *thrdaddr
);
uintptr_t _beginthreadex( // MANAGED CODE
   void *security,
   unsigned stack_size,
   unsigned ( __clrcall *start_address )( void * ),
   void *arglist,
   unsigned initflag,
   unsigned *thrdaddr
);
```

### <a name="parameters"></a>Parametry

*start_address*<br/>
Adres początkowy procedury, która rozpoczyna wykonywanie nowego wątku. W przypadku **_beginthread**Konwencja wywoływania ma wartość [__cdecl](../../cpp/cdecl.md) (dla kodu natywnego) lub [__clrcall](../../cpp/clrcall.md) (dla kodu zarządzanego); w przypadku **_beginthreadex**jest to [__stdcall](../../cpp/stdcall.md) (dla kodu natywnego) lub [__clrcall](../../cpp/clrcall.md) (dla kodu zarządzanego).

*stack_size*<br/>
Rozmiar stosu dla nowego wątku lub 0.

*arglist*<br/>
Lista argumentów, która ma zostać przeniesiona do nowego wątku lub **wartość null**.

*Zabezpieczenia*<br/>
Wskaźnik do struktury [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , który określa, czy zwracany uchwyt może być dziedziczony przez procesy podrzędne. Jeśli *zabezpieczenia* ma **wartość null**, uchwyt nie może być dziedziczony. Musi mieć **wartość null** w przypadku aplikacji dla systemu Windows 95.

*initflag*<br/>
Flagi kontrolujące stan początkowy nowego wątku. Ustaw wartość *initflag* na 0, aby uruchomić ją natychmiast, lub **CREATE_SUSPENDED** , aby utworzyć wątek w stanie wstrzymania. Użyj [ResumeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-resumethread) , aby wykonać wątek. Ustaw flagę *initflag* na **STACK_SIZE_PARAM_IS_A_RESERVATION** , aby użyć *STACK_SIZE* jako początkowego rozmiaru rezerwy stosu w bajtach. Jeśli ta flaga nie jest określona, *stack_size* określa rozmiar zatwierdzania.

*thrdaddr*<br/>
Wskazuje zmienną 32-bitową, która odbiera identyfikator wątku. Jeśli wartość jest **równa null**, nie jest używana.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, każda z tych funkcji zwraca dojście do nowo utworzonego wątku; Jeśli jednak nowo utworzony wątek zostanie zbyt szybko zakończony, **_beginthread** może nie zwrócić prawidłowego dojścia. (Zapoznaj się z dyskusjami w sekcji Uwagi). W przypadku błędu **_beginthread** zwraca wartość-1L, a **errno** jest ustawiony na **EAGAIN** , jeśli istnieje zbyt wiele wątków, do **EINVAL** , jeśli argument jest nieprawidłowy lub rozmiar stosu jest niepoprawny lub do **EACCES** , jeśli są niewystarczające zasoby ( takie jak pamięć). W przypadku błędu funkcja **_beginthreadex** zwraca wartość 0, a **errno** i **_doserrno** są ustawione.

Jeśli *start_address* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL** i Return-1.

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby uzyskać więcej informacji na temat **uintptr_t**, zobacz [typy standardowe](../../c-runtime-library/standard-types.md).

## <a name="remarks"></a>Uwagi

Funkcja **_beginthread** tworzy wątek, który rozpoczyna wykonywanie procedury w *start_address*. Procedura w *start_address* musi używać **__cdecl** (dla kodu natywnego) lub **__clrcall** (dla kodu zarządzanego) i nie powinna mieć wartości zwracanej. Gdy wątek wraca z tej procedury, zostanie automatycznie zakończony. Aby uzyskać więcej informacji na temat wątków, zobacz [Obsługa wielowątkowości dla starszego kodu C++(wizualizacja)](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

**_beginthreadex** przypomina interfejs API [isthread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) Win32 bardziej blisko niż **_beginthread** . **_beginthreadex** różni się od **_beginthread** w następujący sposób:

- **_beginthreadex** ma trzy dodatkowe parametry: *initflag*, *Security*i **threadaddr**. Nowy wątek można utworzyć w stanie wstrzymania z określonym zabezpieczeniami i można uzyskać do niego dostęp przy użyciu *thrdaddr*, który jest identyfikatorem wątku.

- Procedura w *start_address* , która jest przenoszona do **_beginthreadex** , musi używać konwencji wywoływania **__stdcall** (dla kodu natywnego) lub **__clrcall** (dla kodu zarządzanego) i musi zwrócić kod zakończenia wątku.

- **_beginthreadex** zwraca wartość 0 w przypadku niepowodzenia, a nie 1L.

- Wątek, który jest tworzony za pomocą **_beginthreadex** , zostaje zakończony przez wywołanie [_endthreadex](endthread-endthreadex.md).

Funkcja **_beginthreadex** daje większą kontrolę nad sposobem tworzenia wątku niż **_beginthread** . Funkcja **_endthreadex** jest również bardziej elastyczna. Na przykład za pomocą **_beginthreadex**można użyć informacji o zabezpieczeniach, ustawić stan początkowy wątku (uruchomiony lub zawieszony) i uzyskać identyfikator wątku nowo utworzonego wątku. Możesz również użyć uchwytu wątku, który jest zwracany przez **_beginthreadex** z interfejsami API synchronizacji, których nie można zrobić z **_beginthread**.

Korzystanie z programu **_beginthreadex** niż **_beginthread**jest bezpieczniejsze. Jeśli wątek, który jest generowany przez **_beginthread** , zostanie szybko zakończony, uchwyt, który jest zwracany do obiektu wywołującego **_beginthread** , może być nieprawidłowy lub wskazywać na inny wątek. Jednakże uchwyt zwracany przez **_beginthreadex** musi być zamknięty przez obiekt wywołujący **_beginthreadex**, więc jest to prawidłowe dojście, jeśli **_beginthreadex** nie zwróci błędu.

Aby przerwać wątek, można jawnie wywołać [_endthread](endthread-endthreadex.md) lub **_endthreadex** . jednak **_endthread** lub **_endthreadex** jest wywoływana automatycznie, gdy wątek zwraca z procedury, która jest przenoszona jako parametr. Zakończenie wątku z wywołaniem metody **_endthread** lub **_endthreadex** pomaga zapewnić poprawne odzyskiwanie zasobów przyznanych dla wątku.

**_endthread** automatycznie zamyka dojście wątku, a nie **_endthreadex** . W związku z tym, jeśli używasz **_beginthread** i **_endthread**, nie zamykaj jawnie uchwytu wątku, wywołując interfejs API [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) Win32. To zachowanie różni się od interfejsu API Win32 [ExitThread —](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) .

> [!NOTE]
> W przypadku pliku wykonywalnego połączonego z libcmt. lib nie należy wywoływać interfejsu API Win32 **ExitThread —** , aby uniemożliwić odzyskiwanie przydzieloną zasobów przez system czasu wykonywania. **_endthread** i **_endthreadex** Odbierz przydzieloną zasoby wątków, a następnie Wywołaj **ExitThread —** .

System operacyjny obsługuje alokację stosu, gdy wywoływana jest **_beginthread** lub **_beginthreadex** ; nie trzeba przekazywać adresu stosu wątków do żadnej z tych funkcji. Ponadto argument *stack_size* może mieć wartość 0, w takim przypadku system operacyjny używa takiej samej wartości jak stos określony dla wątku głównego.

*arglist* jest parametrem, który ma zostać przesłany do nowo utworzonego wątku. Zwykle jest to adres elementu danych, na przykład ciąg znaków. *arglist* może mieć **wartość null** , jeśli nie jest to konieczne, ale **_beginthread** i **_beginthreadex** muszą mieć określoną wartość do przekazania do nowego wątku. Wszystkie wątki są przerywane, jeśli dowolnych wywołań wątku [Abort](abort.md), **Exit**, **_exit**lub **ExitProcess —** .

Ustawienia regionalne nowego wątku są inicjowane przy użyciu globalnie bieżących informacji o ustawieniach regionalnych dla poszczególnych procesów. Jeśli ustawienia regionalne dla wątku są włączone przez wywołanie [_configthreadlocale](configthreadlocale.md) (globalnie lub tylko dla nowych wątków), wątek może zmienić ustawienia regionalne niezależnie od innych wątków, wywołując metodę **setlocale** lub **_wsetlocale**. Wątki, które nie mają ustawionej flagi ustawień regionalnych dla wątku, mogą mieć wpływ na informacje o ustawieniach regionalnych we wszystkich innych wątkach, które również nie mają ustawionej flagi ustawień regionalnych dla wątku, a także wszystkie nowo utworzone wątki. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

W przypadku kodu/CLR **_beginthread** i **_beginthreadex** mają dwa przeciążenia. Jeden z nich przyjmuje natywny wskaźnik funkcji konwencji wywoływania, a drugi przyjmuje wskaźnik funkcji **__clrcall** . Pierwsze Przeciążenie nie jest bezpieczne dla domeny aplikacji i nigdy nie będzie. Jeśli piszesz kod **/CLR** , musisz upewnić się, że nowy wątek przejdzie do właściwej domeny aplikacji przed uzyskaniem dostępu do zarządzanych zasobów. Można to zrobić na przykład przy użyciu [funkcji call_in_appdomain](../../dotnet/call-in-appdomain-function.md). Drugie Przeciążenie jest bezpieczne dla domeny aplikacji; nowo utworzony wątek zawsze będzie kończyć się w domenie aplikacji obiektu wywołującego **_beginthread** lub **_beginthreadex**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wielowątkowe wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md) .

Aby można było używać **_beginthread** lub **_beginthreadex**, aplikacja musi łączyć się z jedną z wielowątkowych bibliotek wykonawczych języka C.

## <a name="example"></a>Przykład

W poniższym przykładzie zastosowano **_beginthread** i **_endthread**.

```C
// crt_BEGTHRD.C
// compile with: /MT /D "_X86_" /c
// processor: x86
#include <windows.h>
#include <process.h>    /* _beginthread, _endthread */
#include <stddef.h>
#include <stdlib.h>
#include <conio.h>

void Bounce( void * );
void CheckKey( void * );

// GetRandom returns a random integer between min and max.
#define GetRandom( min, max ) ((rand() % (int)(((max) + 1) - (min))) + (min))
// GetGlyph returns a printable ASCII character value
#define GetGlyph( val ) ((char)((val + 32) % 93 + 33))

BOOL repeat = TRUE;                 // Global repeat flag
HANDLE hStdOut;                     // Handle for console window
CONSOLE_SCREEN_BUFFER_INFO csbi;    // Console information structure

int main()
{
    int param = 0;
    int * pparam = &param;

    // Get display screen's text row and column information.
    hStdOut = GetStdHandle( STD_OUTPUT_HANDLE );
    GetConsoleScreenBufferInfo( hStdOut, &csbi );

    // Launch CheckKey thread to check for terminating keystroke.
    _beginthread( CheckKey, 0, NULL );

    // Loop until CheckKey terminates program or 1000 threads created.
    while( repeat && param < 1000 )
    {
        // launch another character thread.
        _beginthread( Bounce, 0, (void *) pparam );

        // increment the thread parameter
        param++;

        // Wait one second between loops.
        Sleep( 1000L );
    }
}

// CheckKey - Thread to wait for a keystroke, then clear repeat flag.
void CheckKey( void * ignored )
{
    _getch();
    repeat = 0;    // _endthread implied
}

// Bounce - Thread to create and control a colored letter that moves
// around on the screen.
//
// Params: parg - the value to create the character from
void Bounce( void * parg )
{
    char       blankcell = 0x20;
    CHAR_INFO  ci;
    COORD      oldcoord, cellsize, origin;
    DWORD      result;
    SMALL_RECT region;

    cellsize.X = cellsize.Y = 1;
    origin.X = origin.Y = 0;

    // Generate location, letter and color attribute from thread argument.
    srand( _threadid );
    oldcoord.X = region.Left = region.Right =
        GetRandom(csbi.srWindow.Left, csbi.srWindow.Right - 1);
    oldcoord.Y = region.Top = region.Bottom =
        GetRandom(csbi.srWindow.Top, csbi.srWindow.Bottom - 1);
    ci.Char.AsciiChar = GetGlyph(*((int *)parg));
    ci.Attributes = GetRandom(1, 15);

    while (repeat)
    {
        // Pause between loops.
        Sleep( 100L );

        // Blank out our old position on the screen, and draw new letter.
        WriteConsoleOutputCharacterA(hStdOut, &blankcell, 1, oldcoord, &result);
        WriteConsoleOutputA(hStdOut, &ci, cellsize, origin, &region);

        // Increment the coordinate for next placement of the block.
        oldcoord.X = region.Left;
        oldcoord.Y = region.Top;
        region.Left = region.Right += GetRandom(-1, 1);
        region.Top = region.Bottom += GetRandom(-1, 1);

        // Correct placement (and beep) if about to go off the screen.
        if (region.Left < csbi.srWindow.Left)
            region.Left = region.Right = csbi.srWindow.Left + 1;
        else if (region.Right >= csbi.srWindow.Right)
            region.Left = region.Right = csbi.srWindow.Right - 2;
        else if (region.Top < csbi.srWindow.Top)
            region.Top = region.Bottom = csbi.srWindow.Top + 1;
        else if (region.Bottom >= csbi.srWindow.Bottom)
            region.Top = region.Bottom = csbi.srWindow.Bottom - 2;

        // If not at a screen border, continue, otherwise beep.
        else
            continue;
        Beep((ci.Char.AsciiChar - 'A') * 100, 175);
    }
    // _endthread given to terminate
    _endthread();
}
```

Naciśnij dowolny klawisz, aby zakończyć przykładową aplikację.

## <a name="example"></a>Przykład

Poniższy przykładowy kod demonstruje, jak można użyć uchwytu wątku, który jest zwracany przez **_beginthreadex** z interfejsem API synchronizacji [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject). Główny wątek czeka na zakończenie drugiego wątku przed kontynuowaniem. Gdy drugi wątek wywołuje **_endthreadex**, powoduje, że obiekt wątku przechodzi do stanu sygnalizującego. Dzięki temu wątek podstawowy będzie kontynuował działanie. Nie można tego zrobić za pomocą **_beginthread** i **_endthread**, ponieważ **_endthread** wywołuje metodę **CloseHandle**, która niszczy obiekt wątku, zanim będzie można ustawić stan sygnalizowanie.

```cpp
// crt_begthrdex.cpp
// compile with: /MT
#include <windows.h>
#include <stdio.h>
#include <process.h>

unsigned Counter;
unsigned __stdcall SecondThreadFunc( void* pArguments )
{
    printf( "In second thread...\n" );

    while ( Counter < 1000000 )
        Counter++;

    _endthreadex( 0 );
    return 0;
}

int main()
{
    HANDLE hThread;
    unsigned threadID;

    printf( "Creating second thread...\n" );

    // Create the second thread.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc, NULL, 0, &threadID );

    // Wait until second thread terminates. If you comment out the line
    // below, Counter will not be correct because the thread has not
    // terminated, and Counter most likely has not been incremented to
    // 1000000 yet.
    WaitForSingleObject( hThread, INFINITE );
    printf( "Counter should be 1000000; it is-> %d\n", Counter );
    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
Creating second thread...
In second thread...
Counter should be 1000000; it is-> 1000000
```

## <a name="see-also"></a>Zobacz także

- [Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)
- [_endthread, _endthreadex](endthread-endthreadex.md)
- [abort](abort.md)
- [exit, _Exit, _exit](exit-exit-exit.md)
- [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
