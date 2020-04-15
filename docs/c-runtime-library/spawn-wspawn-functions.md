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
ms.openlocfilehash: a22f5b0c401dd888bbda451504e644557294544d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322958"
---
# <a name="_spawn-_wspawn-functions"></a>_spawn, _wspawn — Funkcje

Każda z `_spawn` funkcji tworzy i wykonuje nowy proces:

|||
|-|-|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|

Litery na końcu nazwy funkcji określają odmianę.

|Litera|Wariant|
|-|-|
| `e`  | `envp`, tablica wskaźników do ustawień środowiska, jest przekazywana do nowego procesu.  |
| `l`  | Argumenty wiersza polecenia są `_spawn` przekazywane indywidualnie do funkcji. Ten sufiks jest zwykle używany, gdy wiele parametrów do nowego procesu jest znany z wyprzedzeniem.  |
| `p`  | `PATH`zmienna środowiskowa służy do znajdowania pliku do wykonania.  |
| `v`  | `argv`, tablica wskaźników do argumentów wiersza `_spawn` polecenia jest przekazywana do funkcji. Ten sufiks jest zwykle używany, gdy liczba parametrów do nowego procesu jest zmienna.  |

## <a name="remarks"></a>Uwagi

Funkcje, `_spawn` które każdy utworzyć i wykonać nowy proces. Automatycznie obsługują argumenty ciągów wielobajtowych, rozpoznając sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową wielobajtową. Funkcje `_wspawn` są szerokoznakowymi `_spawn` wersjami funkcji; nie obsługują ciągów wielobajtowych znaków. W przeciwnym `_wspawn` razie funkcje `_spawn` zachowują się identycznie jak ich odpowiedniki.

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

Wystarczająca ilość pamięci musi być dostępna do ładowania i wykonywania nowego procesu. Argument `mode` określa działanie podjęte przez proces wywołujący `_spawn`przed i w trakcie . W pliku `mode` Process.h zdefiniowano następujące wartości:

|||
|-|-|
| `_P_OVERLAY`  | Nakłada proces wywołujący z nowym procesem, niszcząc proces wywołujący `_exec` (taki sam efekt jak wywołania).  |
| `_P_WAIT`  | Zawiesza wątek wywołujący do czasu zakończenia wykonywania nowego `_spawn`procesu (synchronicznego).  |
| `_P_NOWAIT` lub `_P_NOWAITO`  | Kontynuuje wykonywanie procesu wywoływania równocześnie z nowym procesem (asynchronicznego). `_spawn`  |
| `_P_DETACH`  | Kontynuuje wykonywanie procesu wywołującego; nowy proces jest uruchamiany w tle bez dostępu do konsoli lub klawiatury. Wywołania `_cwait` przeciwko nowemu procesowi nie `_spawn`powiodą się (asynchroniczne).  |

Argument `cmdname` określa plik, który jest wykonywany jako nowy proces i może określić pełną ścieżkę (z katalogu głównego), ścieżkę częściową (z bieżącego katalogu roboczego) lub po prostu nazwę pliku. Jeśli `cmdname` nie ma rozszerzenia nazwy pliku lub nie kończy się `_spawn` kropką (.), funkcja najpierw próbuje rozszerzenia nazwy pliku .com, a następnie rozszerzenia nazwy pliku .exe, rozszerzenia nazwy pliku .bat, a na końcu rozszerzenia nazwy pliku cmd.

Jeśli `cmdname` ma rozszerzenie nazwy pliku, używane jest tylko to rozszerzenie. Jeśli `cmdname` kończy się kropka, `cmdname` wywołanie wyszukuje `_spawn` bez rozszerzenia nazwy pliku. Funkcja `_spawnlp` `_spawnlpe`, `_spawnvp`i `_spawnvpe` funkcje `cmdname` wyszukują (przy użyciu tych `PATH` samych procedur) w katalogach określonych przez zmienną środowiskową.

Jeśli `cmdname` zawiera specyfikator dysku lub żadnych ukośników (to jest, jeśli jest to ścieżka względna), `_spawn` wywołanie wyszukuje tylko określony plik; wyszukiwanie ścieżek nie jest wykonywane.

W przeszłości niektóre z tych `errno` funkcji ustawiono na zero na sukces; bieżące zachowanie jest `errno` pozostawienie nietknięte na sukces, zgodnie z normą C. Jeśli musisz emulować stare zachowanie, `errno` ustaw na zero tuż przed wywołaniem tych funkcji.

> [!NOTE]
> Aby zapewnić prawidłowe inicjowanie i `setjmp` zakończenie `longjmp` nakładki, nie należy używać funkcji do wprowadzania lub pozostawiania procedury nakładania.

## <a name="arguments-for-the-spawned-process"></a>Argumenty dla procesu zrodzenia

Aby przekazać argumenty do nowego procesu, należy podać jeden lub więcej `_spawn` wskaźników do ciągów znaków jako argumenty w wywołaniu. Te ciągi znaków tworzą listę argumentów dla procesu zduplikowanego. Łączna długość ciągów tworzących listę argumentów dla nowego procesu nie może przekraczać 1024 bajtów. Kończący się znak null ("\0") dla każdego ciągu nie jest uwzględniony w liczbie, ale znaki spacji (automatycznie wstawiane do oddzielnych argumentów) są uwzględniane.

> [!NOTE]
> Spacje osadzone w ciągach mogą powodować nieoczekiwane zachowanie; na przykład `_spawn` przekazanie `"hi there"` ciągu spowoduje, że nowy proces `"hi"` `"there"`otrzyma dwa argumenty i . Jeśli intencją było, aby nowy proces otworzył plik o nazwie "hi there", proces zakończy się niepowodzeniem. Można tego uniknąć, cytując ciąg: `"\"hi there\""`.

> [!IMPORTANT]
> Nie należy przekazywać `_spawn` danych wejściowych użytkownika bez jawnego sprawdzania jego zawartości. `_spawn`spowoduje wywołanie [CreateProcess,](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) więc należy pamiętać, że nazwy ścieżek bez zastrzeżeń może prowadzić do potencjalnych luk w zabezpieczeniach.

Wskaźniki argumentów można przekazać jako `_spawnl`oddzielne `_spawnle` `_spawnlp`argumenty `_spawnlpe`(w , , , i `_spawnv` `_spawnve`) `_spawnvp`lub `_spawnvpe`jako tablica wskaźników (w , , , i ). Musisz przekazać co najmniej `arg0` jeden `argv`argument lub [0] do procesu zrodzenia. Zgodnie z konwencją ten argument jest nazwą programu, jak należy wpisać go w wierszu polecenia. Inna wartość nie powoduje wystąpienia błędu.

, `_spawnl` `_spawnle`, `_spawnlp`i `_spawnlpe` wywołania są zwykle używane w przypadkach, gdy liczba argumentów jest znana z wyprzedzeniem. Argument `arg0` jest zwykle wskaźnikiem do `cmdname`. Argumenty `arg1` za `argn` pośrednictwem są wskaźniki do ciągów znaków tworzących nową listę argumentów. Po `argn`, musi istnieć wskaźnik **NULL,** aby oznaczyć koniec listy argumentów.

, `_spawnv` `_spawnve`, `_spawnvp`i `_spawnvpe` wywołania są przydatne, gdy istnieje zmienna liczba argumentów do nowego procesu. Wskaźniki do argumentów są przekazywane `argv`jako tablica, *.* Argument `argv`[0] jest zwykle wskaźnikiem do ścieżki w trybie rzeczywistym lub `argv`do nazwy programu `argv``n`w trybie chronionym, a [1] przez [ ] są wskaźnikami do ciągów znaków tworzących nową listę argumentów. Argument `argv`[`n` +1] musi być wskaźnikiem **NULL,** aby oznaczyć koniec listy argumentów.

## <a name="environment-of-the-spawned-process"></a>Środowisko procesu zrodzenia

Pliki, które są `_spawn` otwarte po wywołaniu pozostają otwarte w nowym procesie. W `_spawnl`, `_spawnlp` `_spawnv`, `_spawnvp` i wywołania, nowy proces dziedziczy środowisko procesu wywołującego. Można użyć `_spawnle`, `_spawnlpe` `_spawnve`, `_spawnvpe` i wywołania, aby zmienić środowisko dla nowego procesu, przekazując listę ustawień środowiska za pośrednictwem argumentu. `envp` Argument `envp` jest tablicą wskaźników znaków, każdy element (z wyjątkiem elementu końcowego), z których wskazuje ciąg zakończony zerem definiujący zmienną środowiskową. Taki ciąg zwykle ma `NAME` = `value` `NAME` formularz, w którym jest `value` nazwa zmiennej środowiskowej i jest wartością ciągu, do której ustawiona jest ta zmienna. (Uwaga, `value` która nie jest ujęta w cudzysłów podwójnych). Ostatnim elementem `envp` tablicy powinien być **NULL**. Gdy `envp` sam jest **NULL**, zduplikowany proces dziedziczy ustawienia środowiska procesu nadrzędnego.

Funkcje `_spawn` mogą przekazywać wszystkie informacje o otwartych plikach, w tym tryb tłumaczenia, do nowego procesu. Te informacje są przekazywane w `C_FILE_INFO` trybie rzeczywistym za pośrednictwem wpisu w środowisku. Kod startowy zwykle przetwarza ten wpis, a następnie usuwa go ze środowiska. Jednak jeśli `_spawn` funkcja powoduje pojawienie się procesu non-C, ten wpis pozostaje w środowisku. Drukowanie środowiska pokazuje znaki graficzne w ciągu definicji dla tego wpisu, ponieważ informacje o środowisku są przekazywane w postaci binarnej w trybie rzeczywistym. Nie powinno mieć żadnego innego wpływu na normalne operacje. W trybie chronionym informacje o środowisku są przekazywane w formie tekstowej i dlatego nie zawierają znaków graficznych.

Przed wywołaniem `fflush` `_flushall` `_spawn` funkcji należy jawnie opróżnić (używając lub) lub zamknąć dowolny strumień.

Nowe procesy utworzone `_spawn` przez wywołania procedur nie zachowują ustawień sygnału. Zamiast tego zduplikowany proces resetuje ustawienia sygnału do ustawień domyślnych.

## <a name="redirecting-output"></a>Przekierowanie danych wyjściowych

Jeśli dzwonisz `_spawn` z biblioteki DLL lub aplikacji GUI i chcesz przekierować dane wyjściowe do potoku, masz dwie opcje:

- Użyj interfejsu API Win32, aby utworzyć potok, a następnie wywołać [AllocConsole](/windows/console/allocconsole), ustawić wartości uchwytu w strukturze uruchamiania i [wywołać CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw).

- Wywołaj [_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md) który utworzy potok i wywoła aplikację za pomocą **cmd.exe /c** (lub **command.exe /c**).

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

## <a name="see-also"></a>Zobacz też

[Kontrola procesu i środowiska](../c-runtime-library/process-and-environment-control.md)<br/>
[Przerwać](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[_exec, funkcje _wexec](../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_flushall](../c-runtime-library/reference/flushall.md)<br/>
[_getmbcp](../c-runtime-library/reference/getmbcp.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_setmbcp](../c-runtime-library/reference/setmbcp.md)<br/>
[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)
