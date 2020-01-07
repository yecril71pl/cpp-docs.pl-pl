---
title: _spawn, _wspawn — Funkcje
ms.date: 11/04/2016
api_location:
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 81f4bf6c60a0c0e4011536e8d3bc104bbc33e04f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301707"
---
# <a name="_spawn-_wspawn-functions"></a>_spawn, _wspawn — Funkcje

Każda z `_spawn` funkcje tworzy i uruchamia nowy proces:

|||
|-|-|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|

Litery na końcu nazwy funkcji określają odmianę.

|Litera|Wariant|
|-|-|
| `e`  | `envp`, tablica wskaźników do ustawień środowiska, jest przenoszona do nowego procesu.  |
| `l`  | Argumenty wiersza polecenia są przesyłane pojedynczo do funkcji `_spawn`. Ten sufiks jest zwykle używany, gdy kilka parametrów nowego procesu jest znany z wyprzedzeniem.  |
| `p`  | Zmienna środowiskowa `PATH` jest używana do znajdowania pliku do wykonania.  |
| `v`  | `argv`, tablica wskaźników do argumentów wiersza polecenia, jest przenoszona do funkcji `_spawn`. Ten sufiks jest zazwyczaj używany, gdy liczba parametrów nowego procesu jest zmienna.  |

## <a name="remarks"></a>Uwagi

`_spawn` każda funkcja tworzy i uruchamia nowy proces. W razie potrzeby automatycznie obsługują argumenty ciągu znaków wielobajtowych, co pozwala rozpoznać sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową. `_wspawn` funkcje są wersjami znaków dwubajtowych funkcji `_spawn`; nie obsługują one ciągów znaków wielobajtowych. W przeciwnym razie `_wspawn` funkcje zachowują się identycznie z ich `_spawn`nymi odpowiednikami.

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

Do załadowania i wykonania nowego procesu musi być dostępna wystarczająca ilość pamięci. `mode` argument określa akcję podejmowaną przez proces wywołujący przed i podczas `_spawn`. Następujące wartości `mode` są zdefiniowane w procesie. h:

|||
|-|-|
| `_P_OVERLAY`  | Nakłada proces wywołujący z nowym procesem, niszczy proces wywołujący (ten sam efekt w przypadku wywołań `_exec`).  |
| `_P_WAIT`  | Wstrzymuje wątek wywołujący do momentu zakończenia wykonywania nowego procesu (`_spawn`synchroniczna).  |
| `_P_NOWAIT` lub `_P_NOWAITO`  | Kontynuuje wykonywanie procesu wywołującego współbieżnie przy użyciu nowego procesu (`_spawn`asynchroniczne).  |
| `_P_DETACH`  | Kontynuuje wykonywanie procesu wywołującego; nowy proces jest uruchamiany w tle bez dostępu do konsoli lub klawiatury. Wywołania `_cwait` z nowym procesem zakończą się niepowodzeniem (asynchronicznie `_spawn`).  |

`cmdname` argument określa plik, który jest wykonywany jako nowy proces i może określać pełną ścieżkę (z katalogu głównego), ścieżkę częściową (z bieżącego katalogu roboczego) lub tylko nazwę pliku. Jeśli `cmdname` nie ma rozszerzenia nazwy pliku lub nie kończy się kropką (.), funkcja `_spawn` najpierw próbuje rozszerzenie nazwy pliku. com, a następnie rozszerzenie nazwy pliku. exe, rozszerzenie nazwy pliku. bat, a wreszcie rozszerzenie nazwy pliku. cmd.

Jeśli `cmdname` ma rozszerzenie nazwy pliku, używane jest tylko to rozszerzenie. Jeśli `cmdname` kończą się kropką, wywołanie `_spawn` wyszukuje `cmdname` bez rozszerzenia nazwy pliku. Funkcje `_spawnlp`, `_spawnlpe`, `_spawnvp`i `_spawnvpe` szukają `cmdname` (przy użyciu tych samych procedur) w katalogach określonych przez zmienną środowiskową `PATH`.

Jeśli `cmdname` zawiera specyfikator dysku lub dowolne ukośniki (to oznacza, że jeśli jest ścieżką względną), wywołanie `_spawn` wyszukuje tylko określony plik; nie jest wykonywane Wyszukiwanie ścieżek.

W przeszłości niektóre z tych funkcji ustawili `errno` na zero po powodzeniu; bieżące zachowanie polega na pozostawieniu `errno` niezmienionej, zgodnie z opisem w standardzie C. Jeśli zachodzi potrzeba emulowania starego zachowania, należy ustawić `errno` na zero przed wywołaniem tych funkcji.

> [!NOTE]
>  Aby zapewnić prawidłowe Inicjowanie i zakończenie nakładania, nie używaj funkcji `setjmp` ani `longjmp`, aby wprowadzić lub opuścić procedurę nakładki.

## <a name="arguments-for-the-spawned-process"></a>Argumenty dla procesu, który został zduplikowany

Aby przekazać argumenty do nowego procesu, należy nadać co najmniej jeden wskaźnik do ciągów znaków jako argumenty w wywołaniu `_spawn`. Te ciągi znaków tworzą listę argumentów dla procesu, który został zduplikowany. Łączna długość ciągów tworzących listę argumentów dla nowego procesu nie może przekraczać 1024 bajtów. Kończący znak null (' \ 0 ') dla każdego ciągu nie jest uwzględniony w liczbie, ale są uwzględniane znaki spacji (automatycznie wstawione do oddzielnych argumentów).

> [!NOTE]
>  Spacje osadzone w ciągach mogą spowodować nieoczekiwane zachowanie; na przykład przekazywanie `_spawn` ciągu `"hi there"` spowoduje powstanie nowego procesu pobierającego dwa argumenty, `"hi"` i `"there"`. Jeśli chcesz, aby nowy proces otworzył plik o nazwie "Witaj tam", proces zakończy się niepowodzeniem. Można to uniknąć przez wyrażenie Quote ciągu: `"\"hi there\""`.

> [!IMPORTANT]
>  Nie przekazuj danych wejściowych użytkownika do `_spawn` bez jawnego sprawdzenia jego zawartości. `_spawn` spowoduje wywołanie metody [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) , dlatego należy pamiętać, że niekwalifikowane nazwy ścieżek mogą prowadzić do potencjalnych luk w zabezpieczeniach.

Wskaźniki argumentów można przekazać jako oddzielne argumenty (w `_spawnl`, `_spawnle`, `_spawnlp`i `_spawnlpe`) lub jako tablica wskaźników (w `_spawnv`, `_spawnve`, `_spawnvp`i `_spawnvpe`). Należy przekazać co najmniej jeden argument, `arg0` lub `argv`[0] do procesu, który został zduplikowany. Zgodnie z Konwencją, ten argument jest nazwą programu w miarę wpisywania go w wierszu polecenia. Inna wartość nie powoduje błędu.

Wywołania `_spawnl`, `_spawnle`, `_spawnlp`i `_spawnlpe` są zwykle używane w przypadkach, gdy liczba argumentów jest znana z wyprzedzeniem. Argument `arg0` jest zwykle wskaźnikiem do `cmdname`. Argumenty `arg1` za pomocą `argn` są wskaźnikami do ciągów znaków tworzących nową listę argumentów. Poniższe `argn`, aby oznaczyć koniec listy argumentów, musi być **pusty** wskaźnik.

Wywołania `_spawnv`, `_spawnve`, `_spawnvp`i `_spawnvpe` są przydatne, gdy istnieje zmienna liczba argumentów nowego procesu. Wskaźniki do argumentów są przekazane jako tablica, `argv` *.* Argument `argv`[0] jest zwykle wskaźnikiem do ścieżki w trybie rzeczywistym lub do nazwy programu w trybie chronionym, a `argv`[1] przez `argv`[`n`] są wskaźnikami do ciągów znaków tworzących nową listę argumentów. Argument `argv`[`n` + 1] musi być **pustym** wskaźnikiem, aby zaznaczyć koniec listy argumentów.

## <a name="environment-of-the-spawned-process"></a>Środowisko procesu, który został zduplikowany

Pliki, które są otwarte, gdy zostanie utworzone wywołanie `_spawn` w nowym procesie. W ramach wywołań `_spawnl`, `_spawnlp`, `_spawnv`i `_spawnvp` nowy proces dziedziczy środowisko procesu wywołującego. Można użyć wywołań `_spawnle`, `_spawnlpe`, `_spawnve`i `_spawnvpe`, aby zmienić środowisko dla nowego procesu przez przekazanie listy ustawień środowiska za pomocą argumentu `envp`. Argument `envp` jest tablicą wskaźników znaków, każdy element (oprócz elementu końcowego), który wskazuje ciąg zakończony znakiem null definiujący zmienną środowiskową. Taki ciąg ma zwykle postać `NAME`=`value` gdzie `NAME` jest nazwą zmiennej środowiskowej, a `value` to wartość ciągu, do której ta zmienna jest ustawiona. (Należy zauważyć, że `value` nie jest ujęta w znaki podwójnego cudzysłowu). Końcowy element tablicy `envp` powinien mieć **wartość null**. Gdy `envp` jest **równa null**, proces duplikowany dziedziczy ustawienia środowiska procesu nadrzędnego.

Funkcje `_spawn` mogą przekazać wszystkie informacje dotyczące otwartych plików, w tym tryb tłumaczenia, do nowego procesu. Te informacje są przesyłane w trybie rzeczywistym za pomocą wpisu `C_FILE_INFO` w środowisku. Kod uruchamiania zwykle przetwarza ten wpis, a następnie usuwa go ze środowiska. Jeśli jednak funkcja `_spawn` duplikuje proces inny niż C, ten wpis pozostaje w środowisku. Drukowanie środowiska pokazuje znaki graficzne w ciągu definicji dla tego wpisu, ponieważ informacje o środowisku są przesyłane w postaci binarnej w trybie rzeczywistym. Nie powinien mieć żadnego innego wpływu na normalne operacje. W trybie chronionym informacje o środowisku są przesyłane w postaci tekstowej i w związku z tym nie zawierają znaków graficznych.

Musisz jawnie opróżnić (przy użyciu `fflush` lub `_flushall`) lub zamknąć dowolny strumień przed wywołaniem funkcji `_spawn`.

Nowe procesy utworzone przez wywołania do procedur `_spawn` nie zachowują ustawień sygnału. Zamiast tego proces duplikowany resetuje ustawienia sygnału do domyślnego.

## <a name="redirecting-output"></a>Przekierowywanie danych wyjściowych

Jeśli wywołujesz `_spawn` z biblioteki DLL lub aplikacji graficznego interfejsu użytkownika i chcesz przekierować dane wyjściowe do potoku, masz dwie opcje:

- Użyj Win32 API, aby utworzyć potok, następnie Wywołaj [AllocConsole](/windows/console/allocconsole), ustaw wartości dojścia w strukturze uruchamiania i Wywołaj metodę [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw).

- Wywołaj [_popen, _wpopen,](../c-runtime-library/reference/popen-wpopen.md) który utworzy potok i Wywołaj aplikację przy użyciu **cmd. exe/c** (lub **Command. exe/c**).

## <a name="example"></a>Przykład

```c
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

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../c-runtime-library/process-and-environment-control.md)<br/>
[abort](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[_exec, _wexec, funkcje](../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_flushall](../c-runtime-library/reference/flushall.md)<br/>
[_getmbcp](../c-runtime-library/reference/getmbcp.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_setmbcp](../c-runtime-library/reference/setmbcp.md)<br/>
[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)
