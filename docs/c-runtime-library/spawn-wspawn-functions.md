---
title: "_spawn, _wspawn — funkcje | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- _spawn
- _tspawnlp
- _tspawnlpe
- _tspawnve
- _tspawnvp
- _tspawnvpe
- _tspawnl
- spawn
- _tspawnv
- _tspawnle
- wspawn
dev_langs: C++
helpviewer_keywords:
- _tspawnve function
- _spawn functions
- _tspawnlpe function
- tspawnvpe function
- processes, creating
- tspawnve function
- _tspawnvp function
- spawn functions
- tspawnl function
- tspawnlp function
- _tspawnvpe function
- _tspawnl function
- tspawnvp function
- tspawnv function
- processes, executing new
- _tspawnv function
- tspawnle function
- process creation
- _tspawnlp function
- tspawnlpe function
- _tspawnle function
ms.assetid: bb47c703-5216-4e09-8023-8cf25bbf2cf9
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0634aeb37d0374f5e6e1dfae0ac004792c279fc8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="spawn-wspawn-functions"></a>_spawn, _wspawn — Funkcje
Każdy z `_spawn` funkcje tworzy i wykonuje nowy proces:  
  
|||  
|-|-|  
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|  
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|  
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|  
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|  
  
 Liter na końcu nazwy funkcji ustalić zmiany.  
  
 `e`  
 `envp`, tablicy wskaźników do ustawienia środowiska, są przekazywane do nowego procesu.  
  
 `l`  
 Argumenty wiersza polecenia są przekazywane indywidualnie do `_spawn` funkcji. Ten sufiks zazwyczaj jest używany, gdy liczba parametrów do nowego procesu jest znany wcześniej.  
  
 `p`  
 `PATH`Zmienna środowiskowa służy do znajdowania plików do wykonania.  
  
 `v`  
 `argv`, tablicy wskaźników do argumentów wiersza polecenia, są przekazywane do `_spawn` funkcji. Ten sufiks zazwyczaj jest używany, gdy liczba parametrów do nowego procesu jest zmienna.  
  
## <a name="remarks"></a>Uwagi  
 `_spawn` Funkcje każdego tworzenie i wykonywanie nowego procesu. Automatycznie obsługują argumentów ciągów znaków wielobajtowych zgodnie z potrzebami, rozpoznawanie wielobajtowych sekwencji znaków zgodnie ze strony kodowe wielobajtowe obecnie w użyciu. `_wspawn` Funkcje są wersje znaków dwubajtowych `_spawn` działa; nie obsługują ciągi znaków wielobajtowych. W przeciwnym razie `_wspawn` funkcje zachowują się tak samo ich `_spawn` odpowiedniki.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tspawnl`|`_spawnl`|`_spawnl`|`_wspawnl`|  
|`_tspawnle`|`_spawnle`|`_spawnle`|`_wspawnle`|  
|`_tspawnlp`|`_spawnlp`|`_spawnlp`|`_wspawnlp`|  
|`_tspawnlpe`|`_spawnlpe`|`_spawnlpe`|`_wspawnlpe`|  
|`_tspawnv`|`_spawnv`|`_spawnv`|`_wspawnv`|  
|`_tspawnve`|`_spawnve`|`_spawnve`|`_wspawnve`|  
|`_tspawnvp`|`_spawnvp`|`_spawnvp`|`_wspawnvp`|  
|`_tspawnvpe`|`_spawnvpe`|`_spawnvpe`|`_wspawnvpe`|  
  
 Za mało pamięci, muszą być dostępne dla ładowanie i wykonywanie nowego procesu. `mode` Argument określa akcję wykonywaną przez proces wywoływania przed i podczas `_spawn`. Następujące wartości `mode` są zdefiniowane w Process.h:  
  
 `_P_OVERLAY`  
 Nakładki w wywołaniu przetwarzać o nowy proces, proces wywoływania niszczenie (sam wpływ jako `_exec` wywołania).  
  
 `_P_WAIT`  
 Wstrzymuje wątek wywołujący przed zakończeniem wykonywania nowego procesu (synchroniczne `_spawn`).  
  
 `_P_NOWAIT`lub`_P_NOWAITO`  
 Kontynuuje wykonywanie procesu wywołującego równocześnie z nowego procesu (asynchroniczne `_spawn`).  
  
 `_P_DETACH`  
 Kontynuuje wykonywanie proces wywoływania; nowy proces jest uruchomione w tle bez dostępu do konsoli i klawiatury. Wywołuje się `_cwait` względem nowego procesu zakończyć się niepowodzeniem (asynchroniczne `_spawn`).  
  
 `cmdname` Argument określa plik, który jest wykonywany jako nowy proces i określić pełną ścieżkę (z katalogu głównego), ścieżka częściowa (z bieżącego katalogu roboczego) lub po prostu nazwę pliku. Jeśli `cmdname` nie ma rozszerzenie nazwy pliku lub nie kończą się kropką (.), `_spawn` funkcja po raz pierwszy próbuje .com rozszerzenie nazwy pliku, a następnie rozszerzenie nazwy pliku .exe, rozszerzenia nazwy pliku .bat i koniec rozszerzenie nazwy pliku .cmd.  
  
 Jeśli `cmdname` ma rozszerzenie nazwy pliku, tylko że rozszerzenie jest już używane. Jeśli `cmdname` kończy się kropką, `_spawn` wywołać wyszukuje `cmdname` bez rozszerzenia nazwy pliku. `_spawnlp`, `_spawnlpe`, `_spawnvp`, I `_spawnvpe` funkcje wyszukiwania `cmdname` (przy użyciu tych samych procedur) w określonym przez `PATH` zmiennej środowiskowej.  
  
 Jeśli `cmdname` zawiera specyfikator dysku lub dowolnego ukośniki (jeśli jest ścieżką względną), `_spawn` wywołania wyszukuje tylko dla określonego pliku; odbywa się nie ścieżki wyszukiwania.  
  
 W przeszłości, niektóre z tych funkcji zestawu `errno` zero na powodzenie; aktualny efekt jest `errno` niezmienione w przypadku powodzenia, określony przez standard języka C. Aby emulować zachowanie starego należy ustawić `errno` zero bezpośrednio przed wywołaniem funkcji.  
  
> [!NOTE]
>  W celu zapewnienia prawidłowego nakładki inicjowanie i kończenie działania, nie używaj `setjmp` lub `longjmp` funkcji, aby wprowadzić lub pozostaw procedury nakładki.  
  
## <a name="arguments-for-the-spawned-process"></a>Argumenty dla uruchomionego procesu  
 Aby przekazać argumenty do nowego procesu, zapewniają co najmniej jednego wskaźnika do ciągów znaków jako argumenty w `_spawn` wywołania. Te ciągi znaków tworzą listy argumentów działania zduplikowanego procesu. Łączna długość ciągów tworzące listy argumentów dla nowego procesu nie może przekraczać 1024 bajty. Znak końcowy null ('\0') dla każdego ciągu nie jest uwzględnione w liczbie, ale znaków spacji (automatycznie dodaje do oddzielania argumenty) są uwzględniane.  
  
> [!NOTE]
>  Spacji osadzonych w ciągach może spowodować nieoczekiwane zachowanie; na przykład przekazywanie `_spawn` ciąg `"hi there"` spowoduje nowego procesu pobierania dwa argumenty `"hi"` i `"there"`. Jeśli celem ma nowy proces, otwórz plik o nazwie "Cześć", proces nie powiedzie się. Można tego uniknąć przez zamykający ciąg: `"\"hi there\""`.  
  
> [!IMPORTANT]
>  Nie przekazuj danych wejściowych użytkownika na `_spawn` bez jawnie sprawdzania jego zawartości. `_spawn`spowoduje wywołanie [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425) tak należy pamiętać, że ścieżka niekwalifikowanych nazw może prowadzić do potencjalnych luk w zabezpieczeniach.  
  
 Wskaźniki argument można przekazać jako osobne argumentów (w `_spawnl`, `_spawnle`, `_spawnlp`, i `_spawnlpe`) lub w postaci tablicy wskaźników (w `_spawnv`, `_spawnve`, `_spawnvp`, i `_spawnvpe`). Należy podać co najmniej jednego argumentu `arg0` lub `argv`[0], do uruchomionego procesu. Konwencja ten argument jest nazwę programu, należy go wpisać w wierszu polecenia. Inną wartością nie generuje błędu.  
  
 `_spawnl`, `_spawnle`, `_spawnlp`, I `_spawnlpe` wywołania są zazwyczaj używane w przypadku, gdy liczba argumentów jest znany wcześniej. `arg0` Argument jest zwykle wskaźnik do `cmdname`. Argumenty `arg1` za pośrednictwem `argn` są wskaźnikami do ciągów znaków tworzących nowe listy argumentów. Po `argn`, musi istnieć `NULL` wskaźnik do znaku na końcu listy argumentów.  
  
 `_spawnv`, `_spawnve`, `_spawnvp`, I `_spawnvpe` wywołania są przydatne, gdy istnieje zmienna liczba argumentów dla nowego procesu. Wskaźniki do argumenty są przekazywane jako tablica `argv` *.* Argument `argv`[0] jest zwykle wskaźnik do ścieżki w trybie rzeczywistym lub nazwę programu w trybie chronionym i `argv`[1] za pomocą `argv`[`n`] są wskaźnikami do ciągów znaków tworzących nowe listy argumentów. Argument `argv`[`n` + 1] musi być `NULL` wskaźnik do znaku na końcu listy argumentów.  
  
## <a name="environment-of-the-spawned-process"></a>Środowisko uruchomionego procesu  
 Otwórz pliki, które są, kiedy `_spawn` wywołanie pozostają otwarte w nowym procesie. W `_spawnl`, `_spawnlp`, `_spawnv`, i `_spawnvp` wywołań, nowy proces dziedziczy środowisko procesu wywołującego. Można użyć `_spawnle`, `_spawnlpe`, `_spawnve`, i `_spawnvpe` wpływu na środowisko dla nowego procesu przez przekazanie listę ustawień środowiska za pośrednictwem wywołania `envp` argumentu. Argument `envp` jest tablicy wskaźników znak każdego elementu (z wyjątkiem ostatniego elementu), które wskazuje definicji zmiennej środowiskowej ciągu zakończonego wartością null. Taki ciąg ma zazwyczaj postać `NAME` = `value` gdzie `NAME` to nazwa zmiennej środowiskowej i `value` jest wartość ciągu, do którego jest wartość tej zmiennej. (Należy pamiętać, że `value` nie jest ujęta w znaki podwójnego cudzysłowu.) Końcowy element `envp` tablicy powinna być `NULL`. Gdy `envp` jest `NULL`, działania zduplikowanego procesu dziedziczy ustawienia środowiska procesu nadrzędnego.  
  
 `_spawn` Funkcji można przekazać wszystkie informacje o otwartych plików, w tym tryb tłumaczenia, do nowego procesu. Te informacje są przesyłane w trybie rzeczywistym za pomocą `C_FILE_INFO` wpis w środowisku. Kod uruchomienia zwykle przetwarza ten wpis, a następnie usuwa go ze środowiska. Jednak jeśli `_spawn` funkcja spowoduje utworzenie procesu-C, ten wpis pozostanie w środowisku. Drukowanie środowiska pokazuje grafiki znaków w ciągu definicję dla tego wpisu, ponieważ informacje środowiska są przekazywane w postaci binarnej w trybie rzeczywistym. Nie powinna mieć inne wpływ na normalne operacje. W trybie chronionym informacji o środowisku jest przekazywany w formie tekstu i dlatego nie zawiera grafiki znaków.  
  
 Należy jawnie opróżnić (przy użyciu `fflush` lub `_flushall`) lub zamknąć dowolny strumień przed wywołaniem `_spawn` funkcji.  
  
 Nowe procesy utworzone przez wywołania `_spawn` procedury nie zachowuj ustawienia sygnału. Zamiast tego działania zduplikowanego procesu resetuje sygnału ustawienia domyślne.  
  
## <a name="redirecting-output"></a>Przekierowywanie danych wyjściowych  
 Jeśli wywołujesz `_spawn` z biblioteki DLL lub aplikacji do graficznego interfejsu użytkownika i aby przekierować dane wyjściowe do potoku, dostępne są dwie opcje:  
  
-   Utworzyć potok, za pomocą interfejsu API Win32 wywoływać [AllocConsole](http://msdn.microsoft.com/library/windows/desktop/ms681944), ustawić wartości dojścia strukturę uruchamiania i wywołanie [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425).  
  
-   Wywołanie [_popen —, _wpopen —](../c-runtime-library/reference/popen-wpopen.md) co będzie utworzyć potok i wywołać przy użyciu aplikacji **cmd.exe /c** (lub **command.exe /c**).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_spawn.c  
// This program accepts a number in the range  
// 1-8 from the command line. Based on the number it receives,  
// it executes one of the eight different procedures that  
// spawn the process named child. For some of these procedures,  
// the CHILD.EXE file must be in the same directory; for  
// others, it only has to be in the same path.  
//  
  
#include <stdio.h>  
#include <process.h>  
  
char *my_env[] =  
{  
   "THIS=environment will be",  
   "PASSED=to child.exe by the",  
   "_SPAWNLE=and",  
   "_SPAWNLPE=and",  
   "_SPAWNVE=and",  
   "_SPAWNVPE=functions",  
   NULL  
};  
  
int main( int argc, char *argv[] )  
{  
   char *args[4];  
  
   // Set up parameters to be sent:   
   args[0] = "child";  
   args[1] = "spawn??";  
   args[2] = "two";  
   args[3] = NULL;  
  
   if (argc <= 2)  
   {  
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );  
      exit( 1 );  
   }  
  
   switch (argv[1][0])   // Based on first letter of argument   
   {  
   case '1':  
      _spawnl( _P_WAIT, argv[2], argv[2], "_spawnl", "two", NULL );  
      break;  
   case '2':  
      _spawnle( _P_WAIT, argv[2], argv[2], "_spawnle", "two",   
               NULL, my_env );  
      break;  
   case '3':  
      _spawnlp( _P_WAIT, argv[2], argv[2], "_spawnlp", "two", NULL );  
      break;  
   case '4':  
      _spawnlpe( _P_WAIT, argv[2], argv[2], "_spawnlpe", "two",   
                NULL, my_env );  
      break;  
   case '5':  
      _spawnv( _P_OVERLAY, argv[2], args );  
      break;  
   case '6':  
      _spawnve( _P_OVERLAY, argv[2], args, my_env );  
      break;  
   case '7':  
      _spawnvp( _P_OVERLAY, argv[2], args );  
      break;  
   case '8':  
      _spawnvpe( _P_OVERLAY, argv[2], args, my_env );  
      break;  
   default:  
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );  
      exit( 1 );  
   }  
   printf( "from SPAWN!\n" );  
}  
```  
  
```Output  
child process output  
from SPAWN!  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../c-runtime-library/process-and-environment-control.md)   
 [przerwania](../c-runtime-library/reference/abort.md)   
 [atexit —](../c-runtime-library/reference/atexit.md)   
 [_execwexec — funkcje](../c-runtime-library/exec-wexec-functions.md)   
 [exit, _exit — _exit —](../c-runtime-library/reference/exit-exit-exit.md)   
 [_flushall —](../c-runtime-library/reference/flushall.md)   
 [_getmbcp —](../c-runtime-library/reference/getmbcp.md)   
 [_onexit —, _onexit_m —](../c-runtime-library/reference/onexit-onexit-m.md)   
 [_setmbcp —](../c-runtime-library/reference/setmbcp.md)   
 [system, _wsystem](../c-runtime-library/reference/system-wsystem.md)