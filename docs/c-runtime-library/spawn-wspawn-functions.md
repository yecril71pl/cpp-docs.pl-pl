---
title: _spawn, _wspawn — Funkcje
ms.date: 11/04/2016
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
ms.openlocfilehash: caaa3fb40a75292bd32e14ddec33b504e0c1296b
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693717"
---
# <a name="spawn-wspawn-functions"></a>_spawn, _wspawn — Funkcje

Każdy z `_spawn` funkcji tworzy i uruchamia nowy proces:

|||
|-|-|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|

Liter na końcu nazwy funkcji określenia odchylenia.

|Litera|Variant|
|-|-|
| `e`  | `envp`, tablica wskaźników do ustawienia środowiska, jest przekazywany do nowego procesu.  |
| `l`  | Argumenty wiersza polecenia są przekazywane oddzielnie do `_spawn` funkcji. Ten sufiks zwykle jest używana, gdy liczba parametrów do nowego procesu jest znana z wyprzedzeniem.  |
| `p`  | `PATH` Zmienna środowiskowa jest używany do znalezienia pliku do wykonania.  |
| `v`  | `argv`, tablica wskaźników do argumentów wiersza polecenia, jest przekazywany do `_spawn` funkcji. Ten sufiks zwykle jest używana, gdy liczba parametrów do nowego procesu jest zmienna.  |

## <a name="remarks"></a>Uwagi

`_spawn` Funkcje każdego tworzenia i wykonania nowego procesu. Argumenty ciągu znaków wielobajtowych zgodnie z potrzebami, rozpoznawaniu sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową wielobajtowych mogą automatycznie obsługiwać. `_wspawn` Funkcje są wersjami znaków dwubajtowych `_spawn` funkcje; mogą nie obsługiwać ciągi znaków wielobajtowych. W przeciwnym razie `_wspawn` funkcje zachowują się identycznie do ich `_spawn` odpowiedniki.

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

Za mało pamięci, muszą być dostępne dla ładowanie i wykonywanie nowego procesu. `mode` Argument określa akcję podejmowaną przez proces wywołujący, przed, jak i podczas `_spawn`. Następujące wartości dla `mode` są zdefiniowane w Process.h:

|||
|-|-|
| `_P_OVERLAY`  | Nakładki na wywołanie przetwarzania za pomocą nowy proces, niszczenie procesu wywołującego (efektu przez takie same jak `_exec` wywołania).  |
| `_P_WAIT`  | Wstrzymuje działanie wątku wywołującego do momentu wykonania nowego procesu (synchroniczne `_spawn`).  |
| `_P_NOWAIT` lub `_P_NOWAITO`  | Kontynuuje wykonywanie procesu wywołującego wątkom nowego procesu (asynchroniczne `_spawn`).  |
| `_P_DETACH`  | Kontynuuje wykonywanie procesu wywołującego; nowy proces jest uruchamiany w tle bez dostępu do konsoli lub klawiatury. Wywołania `_cwait` względem nowy proces się nie powieść (asynchroniczne `_spawn`).  |

`cmdname` Argument określa plik, który jest wykonywany jako nowy proces i określić pełną ścieżkę (z katalogu głównego), ścieżka częściowa (od bieżącego katalogu roboczego) lub po prostu nazwę pliku. Jeśli `cmdname` nie ma rozszerzenie nazwy pliku lub nie kończą się kropką (.), `_spawn` funkcji po raz pierwszy próbuje .com rozszerzenie nazwy pliku i następnie rozszerzenie nazwy pliku .exe, rozszerzenia nazwy pliku .bat i na koniec rozszerzenie nazwy pliku .cmd.

Jeśli `cmdname` ma rozszerzenie nazwy pliku, tylko że rozszerzenie jest używany. Jeśli `cmdname` kończy się kropką, `_spawn` wywołać wyszukuje `cmdname` bez rozszerzenia nazwy pliku. `_spawnlp`, `_spawnlpe`, `_spawnvp`, I `_spawnvpe` funkcje wyszukiwania `cmdname` (przy użyciu tych samych procedur) w katalogi określone przez `PATH` zmiennej środowiskowej.

Jeśli `cmdname` zawiera specyfikator dysku ani żadnych ukośników (to znaczy, jeśli jest ścieżką względną), `_spawn` wywołanie wyszukiwane są tylko określony plik; odbywa się nie ścieżki wyszukiwania.

W przeszłości, niektóre z tych funkcji set `errno` zero na powodzenie; aktualny efekt jest pozostawienie `errno` niezmienione w przypadku powodzenia, określony przez C standard. Jeśli zachodzi potrzeba emulowanie starsze zachowanie, ustaw `errno` zero tuż przed wywołaniem funkcji.

> [!NOTE]
>  Aby zapewnić właściwe nakładki, inicjowanie i kończenie działania, nie należy używać `setjmp` lub `longjmp` funkcji do wejścia lub wyjścia procedury nakładki.

## <a name="arguments-for-the-spawned-process"></a>Argumenty dla procesu rozmnożonego

Aby przekazać argumenty do nowego procesu, oferowanie co najmniej jednego wskaźnika ciągów znaków jako argumentów w `_spawn` wywołania. Te ciągi znaków formularza listy argumentów dla procesu rozmnożonego. Łączna długość ciągów znaków tworzących listy argumentów nowy proces nie może przekraczać 1024 bajty. Nie ma kończącego znaku null (\0) dla każdego ciągu w liczbie, ale znaków spacji (automatycznie wstawiany do oddzielania argumenty) są uwzględniane.

> [!NOTE]
>  Osadzone w ciągach miejsca do magazynowania może spowodować nieoczekiwane zachowanie; na przykład przekazanie `_spawn` ciąg `"hi there"` spowoduje w nowym procesie pobierania dwa argumenty `"hi"` i `"there"`. Jeśli celem było zapewnienie nowy proces, otwórz plik o nazwie "Cześć", proces może zakończyć się niepowodzeniem. Można tego uniknąć przez cytowanie ciągu: `"\"hi there\""`.

> [!IMPORTANT]
>  Nie przekazuj dane wejściowe użytkownika do `_spawn` jawnie sprawdzeniem jego zawartości. `_spawn` spowoduje wywołanie [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) więc pamiętać o tej ścieżce niekwalifikowanych nazw może prowadzić do potencjalnych luk w zabezpieczeniach.

Można przekazać argument wskaźników jako oddzielne argumenty (w `_spawnl`, `_spawnle`, `_spawnlp`, i `_spawnlpe`) lub jako tablicę wskaźników (w `_spawnv`, `_spawnve`, `_spawnvp`, i `_spawnvpe`). Należy przekazać co najmniej jednego argumentu `arg0` lub `argv`[0] do procesu rozmnożonego. Umownie ten argument jest nazwę programu, należy go wpisać w wierszu polecenia. Inna wartość nie generuje błąd.

`_spawnl`, `_spawnle`, `_spawnlp`, I `_spawnlpe` wywołania są zwykle używane w przypadkach, gdzie liczba argumentów jest znana z wyprzedzeniem. `arg0` Argument jest zazwyczaj wskaźnikiem do `cmdname`. Argumenty `arg1` za pośrednictwem `argn` są wskaźnikami do ciągów znaków tworzących nowe listy argumentów. Następujące `argn`, musi istnieć **NULL** wskaźnik, aby zaznaczyć koniec listy argumentów.

`_spawnv`, `_spawnve`, `_spawnvp`, I `_spawnvpe` wywołania są przydatne w przypadku, gdy ma zmienną liczbę argumentów do nowego procesu. Wskaźniki do argumenty są przekazywane jako tablica, `argv` *.* Argument `argv`[0] jest zazwyczaj wskaźnikiem do ścieżki w trybie rzeczywistym lub nazwy programu w trybie chronionym i `argv`[1] za pomocą `argv`[`n`] są wskaźnikami do ciągów znaków tworzących nowe listy argumentów. Argument `argv`[`n` + 1] musi być **NULL** wskaźnik, aby zaznaczyć koniec listy argumentów.

## <a name="environment-of-the-spawned-process"></a>Środowisko procesu rozmnożonego

Otwórz pliki, które są, kiedy `_spawn` zostanie nawiązane połączenie, pozostają otwarte w nowym procesie. W `_spawnl`, `_spawnlp`, `_spawnv`, i `_spawnvp` wywołań, nowy proces dziedziczy środowisko procesu wywołującego. Możesz użyć `_spawnle`, `_spawnlpe`, `_spawnve`, i `_spawnvpe` wpływu na środowisko, nowy proces, przekazując listę ustawień środowiska za pomocą wywołania `envp` argumentu. Argument `envp` jest tablicą wskaźników znak, której każdy element (z wyjątkiem ostatnim elementem) wskazuje na określenie zmiennej środowiskowej ciąg zakończony znakiem null. Taki ciąg ma zwykle postać `NAME` = `value` gdzie `NAME` to nazwa zmiennej środowiskowej i `value` jest wartość ciągu, do którego ustawiono tę zmienną. (Należy pamiętać, że `value` nie jest ujęty w znaki podwójnego cudzysłowu.) Końcowy element `envp` tablicy powinny być **NULL**. Gdy `envp` jest **NULL**, procesu rozmnożonego dziedziczy ustawienia środowiska dla procesu nadrzędnego.

`_spawn` Funkcji można przekazać wszystkich informacji dotyczących otwartych plików, w tym tryb translacji, do nowego procesu. Te informacje są przesyłane w trybie rzeczywistym za pomocą `C_FILE_INFO` wpis w środowisku. Kod startowy zwykle przetwarza ten wpis, a następnie usuwa je ze środowiska. Jednak jeśli `_spawn` funkcji spowoduje utworzenie procesu-C, ten wpis pozostanie w środowisku. Drukowanie środowiska pokazuje grafiki znaków w ciągu definicji dla tego wpisu, ponieważ informacji o środowisku jest przekazywany w formacie binarnym w trybie rzeczywistym. Nie powinna mieć żadnego innego efektu na normalne operacje. W trybie chronionym informacji o środowisku są przekazywane w postaci tekstu i dlatego nie zawiera żadnych znaków grafiki.

Należy jawnie opróżniania (przy użyciu `fflush` lub `_flushall`) lub zamknąć dowolny strumień przed wywołaniem `_spawn` funkcji.

Nowego procesu utworzonego przez wywołania `_spawn` procedury nie zachowuj ustawienia sygnału. Zamiast tego procesu rozmnożonego Resetuje domyślne ustawienia sygnału.

## <a name="redirecting-output"></a>Przekierowywanie danych wyjściowych

W przypadku wywołania `_spawn` z biblioteki DLL lub graficznego interfejsu użytkownika aplikacji i chcesz przekierować dane wyjściowe do potoku, masz dwie opcje:

- Tworzenie potoku za pomocą interfejsu API Win32 następnie wywołać [AllocConsole](/windows/console/allocconsole), ustaw wartości dojście w strukturze uruchamiania i wywołania [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa).

- Wywołaj [_popen —, _wpopen —](../c-runtime-library/reference/popen-wpopen.md) której utworzysz potok i invoke aplikację za pomocą **cmd.exe /c** (lub **command.exe /c**).

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