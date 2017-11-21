---
title: "_beginthread —, _beginthreadex — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- _beginthread function
- threading [C++], creating threads
- beginthreadex function
- _beginthreadex function
- beginthread function
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
caps.latest.revision: "36"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 88da6a8a34670da588c0fef25b3060c79b3145f8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="beginthread-beginthreadex"></a>_beginthread, _beginthreadex
Tworzy wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `start_address`  
 Początkowy adres procedury, która rozpoczyna się wykonanie nowego wątku. Dla `_beginthread`, jest Konwencja wywoływania [__cdecl](../../cpp/cdecl.md) (dla natywnego kodu) lub [__clrcall](../../cpp/clrcall.md) (dla kodu zarządzanego); w przypadku `_beginthreadex`, jest ona [__stdcall](../../cpp/stdcall.md)(dla natywnego kodu) lub [__clrcall](../../cpp/clrcall.md) (dla zarządzanego kodu).  
  
 `stack_size`  
 Rozmiar stosu dla nowego wątku lub 0.  
  
 `arglist`  
 Lista argumentów do przekazania do nowego wątku lub wartość NULL.  
  
 `Security`  
 Wskaźnik do [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) struktury, która określa, czy zwrócone dojście mogą być dziedziczone przez procesy podrzędne. Jeśli `Security` ma wartość NULL, dojście nie może być dziedziczona. Musi to być wartość NULL dla systemu Windows 95 aplikacji.  
  
 `initflag`  
 Flagi określające początkowy stan nowego wątku. Ustaw `initflag` do `0` natychmiast, uruchomić lub `CREATE_SUSPENDED` można utworzyć wątku, w stanie wstrzymania; użyj [ResumeThread](http://msdn.microsoft.com/library/windows/desktop/ms685086.aspx) do wykonania wątku. Ustaw `initflag` do `STACK_SIZE_PARAM_IS_A_RESERVATION` flagi używania `stack_size` jako początkowa zarezerwowany rozmiar stosu w bajtach; Jeśli ta flaga nie zostanie określony, `stack_size` Określa rozmiar zatwierdzenia.  
  
 `thrdaddr`  
 Wskazuje zmienna 32-bitowego, która odbiera identyfikator wątku. Jeśli ma wartość NULL, nie jest używane.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia, każda z tych funkcji zwraca dojścia do nowo utworzonej wątku; jednak, czy nowo utworzony wątku istnieje zbyt szybko `_beginthread` nie mogą zwracać prawidłowy uchwyt. (Zobacz Omówienie w sekcji uwag.) W przypadku wystąpienia błędu `_beginthread` zwraca L-1 i `errno` ma ustawioną wartość `EAGAIN` jeżeli istnieją zbyt wiele wątków do `EINVAL` argument jest nieprawidłowy lub rozmiar stosu jest niepoprawny, czy do `EACCES` Jeśli za mało zasobów (np. pamięci) . W przypadku wystąpienia błędu `_beginthreadex` zwraca wartość 0, a `errno` i `_doserrno` są ustawione.  
  
 Jeśli `startaddress` ma wartość NULL, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwróć -1.  
  
 Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Aby uzyskać więcej informacji na temat `uintptr_t`, zobacz [standardowych typów](../../c-runtime-library/standard-types.md).  
  
## <a name="remarks"></a>Uwagi  
 `_beginthread` Funkcja tworzy wątku, który rozpoczyna się wykonanie procedury na `start_address`. Procedury w `start_address` należy użyć `__cdecl` (dla natywnego kodu) lub `__clrcall` (dla kodu zarządzanego) konwencji wywoływania i powinna mieć Brak wartości zwracanej. Po powrocie z tej procedury wątku zostanie automatycznie zakończony. Aby uzyskać więcej informacji na temat wątków, zobacz [Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 `_beginthreadex`podobny Win32 [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453.aspx) API więcej ściśle niż `_beginthread` jest. `_beginthreadex`różni się od `_beginthread` w następujący sposób:  
  
-   `_beginthreadex`ma trzy dodatkowe parametry: `initflag`, `security`, i `threadaddr`. Nowego wątku w stanie wstrzymanym, z określonym zabezpieczeń, można tworzyć i jest możliwy za pomocą `thrdaddr`, który jest identyfikatorem wątku.  
  
-   Procedury w `start_address` przekazywany do `_beginthreadex` należy użyć `__stdcall` (dla natywnego kodu) lub `__clrcall` (dla kodu zarządzanego) konwencji wywoływania i musi zwracać kod zakończenia wątku.  
  
-   `_beginthreadex`Zwraca wartość 0, niepowodzenia zamiast L-1.  
  
-   Wątek, który jest tworzony przy użyciu `_beginthreadex` zostało zakończone przez wywołanie do [_endthreadex —](../../c-runtime-library/reference/endthread-endthreadex.md).  
  
 `_beginthreadex` Funkcja zapewnia większą kontrolę nad procesem tworzenia wątku niż `_beginthread` jest. `_endthreadex` Funkcja jest również bardziej elastyczne. Na przykład z `_beginthreadex`, użyj informacji dotyczących zabezpieczeń, ustaw początkowy stan wątku (uruchomiona lub wstrzymana) i Pobierz identyfikator wątku nowo utworzony wątku. Można również użyć dojście wątku, który jest zwracany przez `_beginthreadex` przy synchronizacji interfejsów API, które nie `_beginthread`.  
  
 Jest bezpieczniejsze w użyciu `_beginthreadex` niż `_beginthread`. Jeśli wątek, który jest generowany przez `_beginthread` kończy się szybko, dojście, która jest zwracana do wywołującego `_beginthread` może być nieprawidłowy lub wskaż inny wątek. Jednak zwracany przez dojście `_beginthreadex` zamknąć przez obiekt wywołujący `_beginthreadex`, więc jego gwarantuje to prawidłowe, jeśli `_beginthreadex` nie zwrócił błąd.  
  
 Możesz wywołać [_endthread —](../../c-runtime-library/reference/endthread-endthreadex.md) lub `_endthreadex` jawnie na zakończenie wątku; jednak `_endthread` lub `_endthreadex` automatycznie jest wywoływane, gdy wątek zwraca z procedury, która została przekazana jako parametr. Przerywanie wątków w wyniku wywołania `_endthread` lub `_endthreadex` pomaga zapewnić poprawne odzyskiwania zasobów przydzielonych dla wątku.  
  
 `_endthread`konieczne jest automatycznie zamykany dojście wątku `_endthreadex` nie. W związku z tym, kiedy należy używać `_beginthread` i `_endthread`, nie zamykaj jawnie dojście wątku przez wywołanie Win32 [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) interfejsu API. To zachowanie różni się od środowiska Win32 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659.aspx) interfejsu API.  
  
> [!NOTE]
>  Dla pliku wykonywalnego połączone z Libcmt.lib, nie należy wywoływać Win32 `ExitThread` interfejsu API, aby nie uniemożliwiają odzyskiwanie przez system środowiska wykonawczego przydzielone zasoby. `_endthread`i `_endthreadex` odzyskać wątku przydzielone zasoby, a następnie wywołać `ExitThread`.  
  
 Alokacja stosu obsługi systemu operacyjnego podczas albo `_beginthread` lub `_beginthreadex` nazywa się; nie trzeba przekazać adres stosu wątku do jednej z tych funkcji. Ponadto `stack_size` argument może być 0, w którym w przypadku systemu operacyjnego korzysta z tej samej wartości jako stosu, który jest określony wątku głównego.  
  
 `arglist`jest to parametr do przekazania do nowo utworzonej wątku. Zazwyczaj jest to adres elementu danych, takiego jak ciąg znaków. `arglist`może mieć wartość NULL, jeśli nie jest wymagana, ale `_beginthread` i `_beginthreadex` należy podać niektóre wartości do przekazania do nowego wątku. Wszystkie wątki są zakończone, jeśli żadnego wątku wywołania `abort`, `exit`, `_exit`, lub `ExitProcess`.  
  
 Ustawienia regionalne nowego wątku jest dziedziczona z wątku jej nadrzędnej. Jeśli ustawienia regionalne dla każdego wątku jest włączona przez wywołanie do [_configthreadlocale —](../../c-runtime-library/reference/configthreadlocale.md) (globalnie lub dla nowych wątków), Wątek można zmieniać tylko jego ustawienia regionalne niezależnie od jego elementu nadrzędnego, wywołując `setlocale` lub `_wsetlocale`. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Kod mieszany i czystego `_beginthread` i `_beginthreadex` mieć dwa przeciążenia — wskaźnik funkcji macierzystej Konwencja wywoływania, inne ma wyższy `__clrcall` wskaźnik funkcji. Pierwszy przeciążenia nie jest bezpieczne dla domeny aplikacji i nigdy nie będzie można. Podczas pisania kodu mieszanych lub czystej należy się upewnić, że nowego wątku wprowadza domeny właściwej aplikacji przed uzyskuje dostęp do zasobów zarządzanych. Można to zrobić, na przykład za pomocą [call_in_appdomain — funkcja](../../dotnet/call-in-appdomain-function.md). Drugi przeciążenie to aplikacja bezpieczne domeny; nowo utworzony wątku zawsze kończy się do domeny aplikacji obiektu wywołującego z `_beginthread` lub `_beginthreadex`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_beginthread`|\<process.h >|  
|`_beginthreadex`|\<process.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wielowątkowe wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
 Aby użyć `_beginthread` lub `_beginthreadex`, aplikacja musi łączyć się z jednym z wielowątkowe biblioteki wykonawcze języka C.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `_beginthread` i `_endthread`.  
  
```  
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
  
// Bounce - Thread to create and and control a colored letter that moves  
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
  
 Naciśnij dowolny klawisz, aby zakończyć przykładowej aplikacji.  
  
## <a name="example"></a>Przykład  
 Następujący przykładowy kod pokazuje, jak używasz dojście wątku, który jest zwracany przez `_beginthreadex` przy synchronizacji interfejsu API [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032.aspx). Wątku głównego czeka na zakończenie przed kontynuowaniem drugiego wątku. Podczas drugiego wątku wywołuje `_endthreadex`, powoduje jego obiekt wątku przejść do stanu sygnałowego. Dzięki temu podstawowy wątku z działającym systemem. Nie można tego dokonać z `_beginthread` i `_endthread`, ponieważ `_endthread` wywołania `CloseHandle`, który niszczy obiekt wątku przed można ustawić stan sygnałowego.  
  
```  
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
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [_endthread —, _endthreadex —](../../c-runtime-library/reference/endthread-endthreadex.md)   
 [przerwania](../../c-runtime-library/reference/abort.md)   
 [exit, _exit — _exit —](../../c-runtime-library/reference/exit-exit-exit.md)   
 [Funkcja GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190)