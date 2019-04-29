---
title: _beginthread, _beginthreadex
ms.date: 02/27/2018
apiname:
- _beginthread
- _beginthreadex
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: d70d2fb0ecb647d4854a6277d6c69cd9886e072f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349267"
---
# <a name="beginthread-beginthreadex"></a>_beginthread, _beginthreadex

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
Początkowy adres procedury, która rozpoczyna wykonywanie nowego wątku. Aby uzyskać **_beginthread**, konwencja wywołania to [__cdecl](../../cpp/cdecl.md) (dla kodu natywnego) lub [__clrcall](../../cpp/clrcall.md) (dla kodu zarządzanego); w przypadku **_beginthreadex**, jest ona [__stdcall](../../cpp/stdcall.md) (dla kodu natywnego) lub [__clrcall](../../cpp/clrcall.md) (dla kodu zarządzanego).

*stack_size*<br/>
Rozmiar stosu dla nowego wątku lub 0.

*arglist*<br/>
Lista argumentów do przekazania do nowego wątku lub **NULL**.

*Zabezpieczenia*<br/>
Wskaźnik do [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) strukturę, która określa, czy zwracany uchwyt może być dziedziczony przez procesy podrzędne. Jeśli *zabezpieczeń* jest **NULL**, uchwyt nie może być dziedziczona. Musi być **NULL** dla aplikacji Windows 95.

*initflag*<br/>
Flagi określające początkowy stan nowego wątku. Ustaw *initflag* do 0, aby natychmiast uruchomić lub **CREATE_SUSPENDED** można utworzyć wątku w stanie wstrzymania; użyj [ResumeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-resumethread) realizować wątek. Ustaw *initflag* do **STACK_SIZE_PARAM_IS_A_RESERVATION** flagi używania *stack_size* zgodnie z pierwszym zarezerwować rozmiar stosu w bajtach; Jeśli ta flaga jest nieokreślona, *stack_size* Określa rozmiar zatwierdzenia.

*thrdaddr*<br/>
Wskazuje zmienną 32-bitową, która odbiera identyfikator wątku. Jeśli jest **NULL**, nie jest używany.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, każda z tych funkcji zwraca uchwyt do nowo utworzonego wątku; Jednakże, jeśli nowo utworzony wątek kończy działanie zbyt szybko **_beginthread** może nie zwrócić prawidłowego uchwytu. (Zobacz Omówienie w sekcja uwagi). W przypadku błędu **_beginthread** zwraca-1 L i **errno** ustawiono **EAGAIN** w przypadku zbyt wiele wątków do **EINVAL** Jeśli argument jest nieprawidłowy lub rozmiar stosu jest niepoprawny, lub **EACCES** przypadku niewystarczających zasobów (takich jak pamięć). W przypadku błędu **_beginthreadex** zwraca wartość 0, a **errno** i **_doserrno** są ustawione.

Jeśli *start_address* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają wartość -1.

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby uzyskać więcej informacji na temat **uintptr_t —**, zobacz [standardowych typów](../../c-runtime-library/standard-types.md).

## <a name="remarks"></a>Uwagi

**_Beginthread** funkcja tworzy wątek, który rozpoczyna wykonywanie procedury w *start_address*. Procedura w *start_address* należy użyć **__cdecl** (dla kodu natywnego) lub **__clrcall** (dla kodu zarządzanego) konwencji wywoływania i powinna posiadać wartości zwrotnej. Kiedy wątek wraca z tej procedury, jest automatycznie kończony. Aby uzyskać więcej informacji na temat wątków zobacz [Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

**_beginthreadex** podobny Win32 [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) API więcej niż ściśle **_beginthread** jest. **_beginthreadex** różni się od **_beginthread** w następujący sposób:

- **_beginthreadex** ma trzy dodatkowe parametry: *initflag*, *zabezpieczeń*, i **threadaddr**. Nowy wątek mogą być tworzone w stanie wstrzymania, z określonymi zabezpieczeniami i jest możliwy za pomocą *thrdaddr*, który jest identyfikatorem wątku.

- Procedura w *start_address* przekazana do **_beginthreadex** należy użyć **__stdcall** (dla kodu natywnego) lub **__clrcall** (dla kod zarządzany) konwencji wywoływania i musi zwrócić kod wyjścia wątku.

- **_beginthreadex** zwraca wartość 0-1 L, a nie awarii.

- Wątek, który jest tworzony przy użyciu **_beginthreadex** jest zakończony przez wywołanie [_endthreadex](endthread-endthreadex.md).

**_Beginthreadex** funkcja daje większą kontrolę nad procesem tworzenia wątku niż **_beginthread** jest. **_Endthreadex** funkcja jest również bardziej elastyczna. Na przykład za pomocą **_beginthreadex**, możesz użyć informacji o zabezpieczeniach, ustawić stan początkowy wątku (uruchomiony lub zawieszony) i uzyskać identyfikator wątku dla nowo utworzonego wątku. Można również użyć uchwytu wątku, który jest zwracany przez **_beginthreadex** z API synchronizacji, czego nie możesz zrobić za pomocą **_beginthread**.

Bezpieczniej jest używać **_beginthreadex** niż **_beginthread**. Jeśli wątek, który jest generowany przez **_beginthread** szybko się zamyka, uchwyt, który jest zwracany do obiektu wywołującego **_beginthread** może być nieprawidłowy lub wskazywać na inny wątek. Jednakże uchwyt zwracany przez **_beginthreadex** musi być zamknięty przez obiekt wywołujący **_beginthreadex**, więc jest gwarantowane jako prawidłowe, jeśli **_beginthreadex** nie zwrócił błąd.

Możesz wywołać [_endthread](endthread-endthreadex.md) lub **_endthreadex** jawnie, aby zakończyć wątek; jednak **_endthread** lub **_endthreadex** nosi nazwę automatycznie kiedy wątek wraca z procedury, która jest przekazywana jako parametr. Zakończenie wątku z wywołaniem **_endthread** lub **_endthreadex** pomaga zapewnić poprawny odzysk zasobów, które są przydzielane do wątku.

**_endthread** automatycznie zamyka uchwyt do wątku, natomiast **_endthreadex** nie. W związku z tym, kiedy używasz **_beginthread** i **_endthread**, nie zamykaj jawnie uchwytu wątku poprzez wywołanie Win32 [funkcja CloseHandle](/windows/desktop/api/handleapi/nf-handleapi-closehandle) interfejsu API. To zachowanie różni się od Win32 [ExitThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitthread) interfejsu API.

> [!NOTE]
> Dla pliku wykonywalnego połączonego z Libcmt.lib Nie wywołuj Win32 **ExitThread** interfejsu API, aby nie uniemożliwiają odzyskiwanie przez system środowiska wykonawczego przydzielone zasoby. **_endthread** i **_endthreadex** odzyskiwania zasobów przydzielonych wątku, a następnie wywołać **ExitThread**.

System operacyjny obsługuje alokację stosu przy albo **_beginthread** lub **_beginthreadex** nosi nazwę; nie trzeba przekazywać adresu stosu wątku do żadnej z tych funkcji. Ponadto *stack_size* argument może przyjąć wartość 0, w którym przypadku system operacyjny używa tej samej wartości co stos, który jest określony wątku głównego.

*lista_argumentów* jest parametrem, który zostanie przekazany do nowo utworzonego wątku. Zazwyczaj jest adres elementu danych, takich jak ciąg znaków. *lista_argumentów* może być **NULL** Jeśli nie jest wymagana, ale **_beginthread** i **_beginthreadex** muszą mieć jakąś wartość do przekazania do nowego wątku. Wszystkie wątki są kończone, jeżeli dowolny wątek jest wywołany [przerwać](abort.md), **wyjść**, **_exit**, lub **exitprocess —**.

Ustawienia regionalne nowego wątku jest inicjowana przy użyciu każdego procesu globalnego bieżące informacje o ustawieniach regionalnych. Jeśli ustawienia regionalne na wątek jest włączony przez wywołanie [_configthreadlocale](configthreadlocale.md) (globalnie albo dla nowych wątków tylko), wątek może zmieniać jego ustawienia regionalne niezależnie od innych wątków przez wywołanie metody **setlocale** lub **_wsetlocale**. Wątki, które nie mają Ustaw flagę ustawień regionalnych na wątek może mieć wpływ na informacje o ustawieniach regionalnych w wszystkie wątki, które nie mają również ustawić flagę ustawień regionalnych na wątek, a także wszystkie nowo utworzone wątki. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Aby uzyskać **/CLR** kodu, **_beginthread** i **_beginthreadex** mają po dwa przeciążenia. Jedno wykorzystuje wskaźnik natywnej funkcji Konwencji, a drugi zajmuje **__clrcall** wskaźnika funkcji. Pierwsze przeciążenie nie jest bezpieczny dla domeny aplikacji i nigdy nie będzie można. Jeśli piszesz **/CLR** kodu, należy upewnić się, że nowy wątek wchodzi do prawidłowej domeny aplikacji przed uzyskuje dostęp do zarządzanych zasobów. Można to zrobisz, na przykład za pomocą [call_in_appdomain, funkcja](../../dotnet/call-in-appdomain-function.md). Drugie przeciążenie to sejf domeny; aplikacji nowo utworzony wątek zawsze zakończy się się w domenie aplikacji wywołującego **_beginthread** lub **_beginthreadex**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wielowątkowe wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

Aby użyć **_beginthread** lub **_beginthreadex**, aplikacja musi łączyć z jedną z wielowątkowych bibliotek środowiska uruchomieniowego C.

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

Poniższy przykład kodu demonstruje, jak można użyć uchwytu wątku, który jest zwracany przez **_beginthreadex** z synchronizacją API [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject). Główny wątek czeka na zakończenie przed kontynuowaniem drugiego wątku. Kiedy drugi wątek wywołuje **_endthreadex**, sprawia, że jego obiekt wątku przejść do sygnalizowanego stanu. Pozwala to głównemu wątkowi kontynuować działanie. Nie można tego zrobić za pomocą **_beginthread** i **_endthread**, ponieważ **_endthread** wywołania **funkcja CloseHandle**, co niszczy wątku obiekt, zanim może zostać ustawiony na zasygnalizowany stan.

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
- [GetExitCodeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
