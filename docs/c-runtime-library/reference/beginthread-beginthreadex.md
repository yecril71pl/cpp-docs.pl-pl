---
title: _beginthread, _beginthreadex
ms.date: 4/2/2020
api_name:
- _beginthread
- _beginthreadex
- _o__beginthread
- _o__beginthreadex
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 2d2851a7e76a43501145b1e55e8028b72c2a8afb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348673"
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
Uruchom adres procedury, która rozpoczyna wykonywanie nowego wątku. W **przypadku _beginthread**konwencja wywołująca jest [__cdecl](../../cpp/cdecl.md) (dla kodu macierzystego) lub [__clrcall](../../cpp/clrcall.md) (dla kodu zarządzanego); dla **_beginthreadex**, jest to [__stdcall](../../cpp/stdcall.md) (dla kodu macierzystego) lub [__clrcall](../../cpp/clrcall.md) (dla kodu zarządzanego).

*stack_size*<br/>
Rozmiar stosu dla nowego wątku lub 0.

*arglista*<br/>
Lista argumentów, które mają zostać przekazane do nowego wątku lub **NULL**.

*Zabezpieczenia*<br/>
Wskaźnik do [struktury SECURITY_ATTRIBUTES,](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) która określa, czy zwrócony uchwyt może być dziedziczony przez procesy podrzędne. Jeśli *wartość Security* ma wartość **NULL,** uchwyt nie może być dziedziczony. Musi być **null** dla aplikacji systemu Windows 95.

*initflag*<br/>
Flagi, które kontrolują stan początkowy nowego wątku. Ustaw *initflag* na 0, aby uruchomić natychmiast lub **CREATE_SUSPENDED,** aby utworzyć wątek w stanie wstrzymanym; użyj [ResumeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-resumethread) do wykonania wątku. Ustaw *flagę initflag,* aby **STACK_SIZE_PARAM_IS_A_RESERVATION** flagę, aby użyć *stack_size* jako początkowego rozmiaru rezerwy stosu w bajtach; jeśli ta flaga nie jest określona, *stack_size* określa rozmiar zatwierdzenia.

*thrdaddr*<br/>
Wskazuje zmienną 32-bitową, która odbiera identyfikator wątku. Jeśli **jest**null , nie jest używany.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, każda z tych funkcji zwraca dojście do nowo utworzonego wątku; jednak jeśli nowo utworzony wątek kończy działanie zbyt szybko, **_beginthread** może nie zwrócić prawidłowego dojścia. (Zobacz dyskusję w sekcji Uwagi). W przypadku błędu **_beginthread** zwraca -1L, a **errno** jest ustawiona na **EAGAIN,** jeśli istnieje zbyt wiele wątków, do **EINVAL,** jeśli argument jest nieprawidłowy lub rozmiar stosu jest niepoprawny, lub **do EACCES,** jeśli nie ma wystarczających zasobów (takich jak pamięć). W razie błędu **_beginthreadex** zwraca wartość 0, a **errno** i **_doserrno** są ustawione.

Jeśli *start_address* ma **wartość NULL,** wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w programie [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje ustawić **errno** na **EINVAL** i zwracać -1.

Aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby uzyskać więcej informacji na temat **uintptr_t**, zobacz [Typy standardowe](../../c-runtime-library/standard-types.md).

## <a name="remarks"></a>Uwagi

Funkcja **_beginthread** tworzy wątek, który rozpoczyna wykonywanie procedury w *start_address*. Procedura w *start_address* musi używać **__cdecl** (dla kodu macierzystego) lub **__clrcall** (dla kodu zarządzanego) wywołanie konwencji i nie powinien mieć wartość zwracaną. Gdy wątek powraca z tej procedury, jest automatycznie kończony. Aby uzyskać więcej informacji na temat wątków, zobacz [Obsługa wielowątkowej obsługi starszego kodu (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

**_beginthreadex** przypomina interfejs API Tworzenia [Wyd](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) **_beginthread.** **_beginthreadex** różni się od **_beginthread** w następujący sposób:

- **_beginthreadex** ma trzy dodatkowe parametry: *initflag*, *Security*i **threadaddr**. Nowy wątek może być utworzony w stanie wstrzymania, z określonymi zabezpieczeniami i można uzyskać do niego dostęp za pomocą *thrdaddr*, który jest identyfikatorem wątku.

- Procedura w *start_address,* który jest przekazywany do **_beginthreadex** musi używać **__stdcall** (dla kodu macierzystego) lub **__clrcall** (dla kodu zarządzanego) wywołanie konwencji i musi zwrócić kod zakończenia wątku.

- **_beginthreadex** zwraca 0 na błąd, a nie -1L.

- Wątek, który jest tworzony przy użyciu **_beginthreadex** jest kończony przez wywołanie [_endthreadex](endthread-endthreadex.md).

Funkcja **_beginthreadex** zapewnia większą kontrolę nad tworzeniem wątku niż **_beginthread.** Funkcja **_endthreadex** jest również bardziej elastyczna. Na przykład z **_beginthreadex**, można użyć informacji o zabezpieczeniach, ustawić początkowy stan wątku (uruchomiony lub zawieszony) i uzyskać identyfikator wątku nowo utworzonego wątku. Można również użyć uchwytu wątku, który jest zwracany przez **_beginthreadex** z interfejsami API synchronizacji, których nie można zrobić z **_beginthread**.

Bezpieczniej jest używać **_beginthreadex** niż **_beginthread.** Jeśli wątek, który jest generowany przez **_beginthread** kończy się szybko, dojście, który jest zwracany do wywołującego **_beginthread** może być nieprawidłowy lub wskazać inny wątek. Jednak dojście, który jest zwracany przez **_beginthreadex** musi zostać zamknięty przez obiekt wywołujący **_beginthreadex**, więc jest gwarantowane jako prawidłowy dojście, jeśli **_beginthreadex** nie zwrócił błędu.

Można wywołać [_endthread](endthread-endthreadex.md) lub **_endthreadex** jawnie, aby zakończyć wątek; jednak **_endthread** lub **_endthreadex** jest wywoływana automatycznie, gdy wątek zwraca z procedury, która jest przekazywana jako parametr. Zakończenie wątku wywołaniem **_endthread** lub **_endthreadex** pomaga zapewnić poprawne odzyskiwanie zasobów, które są przydzielone dla wątku.

**_endthread** automatycznie zamyka uchwyt wątku, natomiast **_endthreadex** nie. W związku z tym podczas korzystania **z _beginthread** i **_endthread**, nie jawnie zamknąć dojście wątku, wywołując Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) INTERFEJSU API. To zachowanie różni się od interfejsu API [Win32 ExitThread.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread)

> [!NOTE]
> W przypadku pliku wykonywalnego połączonego z libcmt.lib nie należy wywoływać interfejsu API **Win32 ExitThread,** aby nie uniemożliwiać systemowi wykonywania odzyskiwania przydzielonych zasobów. **_endthread** i **_endthreadex** odzyskać przydzielone zasoby wątku, a następnie **wywołać ExitThread**.

System operacyjny obsługuje alokacji stosu, gdy **wywoływana** jest _beginthread lub **_beginthreadex;** nie trzeba przekazywać adres stosu wątków do jednej z tych funkcji. Ponadto argument *stack_size* może być 0, w którym to przypadku system operacyjny używa tej samej wartości co stos, który jest określony dla wątku głównego.

*arglist* jest parametrem, który ma być przekazany do nowo utworzonego wątku. Zazwyczaj jest to adres elementu danych, takich jak ciąg znaków. *arglist* może być **null,** jeśli nie jest potrzebne, ale **_beginthread** i **_beginthreadex** musi mieć pewną wartość do przekazania do nowego wątku. Wszystkie wątki są kończone, jeśli dowolny wątek wywołuje [przerwać,](abort.md) **zakończyć,** **_exit**lub **ExitProcess**.

Ustawienia regionalne nowego wątku są inicjowane przy użyciu informacji o bieżących ustawieniach regionalnych dla procesu. Jeśli ustawienia regionalne dla wątku jest włączona przez wywołanie [_configthreadlocale](configthreadlocale.md) (globalnie lub tylko dla nowych wątków), wątek może zmienić swoje ustawienia regionalne niezależnie od innych wątków, wywołując **setlocale** lub **_wsetlocale**. Wątki, które nie mają ustawienia regionalne dla wątku zestaw flag może mieć wpływ na informacje o ustawieniach regionalnych we wszystkich innych wątków, które również nie mają ustawienia regionalne na wątek flagi, a także wszystkie nowo utworzone wątki. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Dla **/clr** **kod, _beginthread** i **_beginthreadex** każdy ma dwa przeciążenia. Jeden przyjmuje wskaźnik funkcji natywnej konwencji wywoływania, a drugi przyjmuje wskaźnik funkcji **__clrcall.** Pierwsze przeciążenie nie jest bezpieczne dla domeny aplikacji i nigdy nie będzie. Jeśli piszesz **/clr** kod należy upewnić się, że nowy wątek wchodzi do domeny poprawnej aplikacji, zanim uzyskuje dostęp do zasobów zarządzanych. Można to zrobić, na przykład, za pomocą [funkcji call_in_appdomain](../../dotnet/call-in-appdomain-function.md). Drugie przeciążenie jest bezpieczne dla domeny aplikacji; nowo utworzony wątek zawsze znajdzie się w domenie aplikacji wywołującego **_beginthread** lub **_beginthreadex**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_beginthread**|\<> proces.h|
|**_beginthreadex**|\<> proces.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wielowątkowe wersje [tylko bibliotek w czasie wykonywania języka C.](../../c-runtime-library/crt-library-features.md)

Aby użyć **_beginthread** lub **_beginthreadex,** aplikacja musi połączyć się z jedną z wielowątkowe biblioteki wyładowywać C.

## <a name="example"></a>Przykład

W poniższym przykładzie użyto **_beginthread** i **_endthread**.

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

Poniższy przykładowy kod pokazuje, jak można użyć dojścia wątku, który jest zwracany przez **_beginthreadex** z interfejsem API synchronizacji [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject). Główny wątek czeka na drugi wątek, aby zakończyć przed kontynuowaniem. Gdy drugi wątek wywołuje **_endthreadex**, powoduje, że jego obiekt wątku, aby przejść do stanu sygnalizowane. Dzięki temu wątek podstawowy, aby kontynuować uruchamianie. Nie można tego zrobić za pomocą **_beginthread** i **_endthread**, ponieważ **_endthread** wywołuje **CloseHandle**, który niszczy obiekt wątku, zanim będzie można ustawić stan sygnalizowany.

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

## <a name="see-also"></a>Zobacz też

- [Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)
- [_endthread, _endthreadex](endthread-endthreadex.md)
- [Przerwać](abort.md)
- [exit, _Exit, _exit](exit-exit-exit.md)
- [GetExitCodeThread (GetExitCodeThread)](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
