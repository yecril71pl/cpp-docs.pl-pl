---
title: _exec, _wexec — Funkcje
ms.date: 11/04/2016
apilocation:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _texecve
- texecl
- _texeclpe
- texecve
- texecv
- texeclp
- texecle
- exec
- texeclpe
- _texecvp
- _texecl
- _texecle
- wexec
- _exec
- _texeclp
- _texecvpe
- texecvpe
- _texecv
- _wexec
helpviewer_keywords:
- _texecle function
- _texecv function
- texeclpe function
- texecle function
- _texecl function
- texecv function
- _texeclp function
- _texecve function
- texecl function
- texecve function
- exec function
- texeclp function
- texecvp function
- texecvpe function
- processes, executing new
- _texecvp function
- _texeclpe function
- _wexec functions
- wexec functions
- _exec function
- _texecvpe function
ms.assetid: a261df93-206a-4fdc-b8ac-66aa7db83bc6
ms.openlocfilehash: 4974571764c22b26e84e93c68d679afc8a1cea73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573371"
---
# <a name="exec-wexec-functions"></a>_exec, _wexec — Funkcje

Każda funkcja w tej rodzinie ładuje i uruchamia nowy proces:

|||
|-|-|
|[_execl, _wexecl](../c-runtime-library/reference/execl-wexecl.md)|[_execv, _wexecv](../c-runtime-library/reference/execv-wexecv.md)|
|[_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)|[_execve, _wexecve](../c-runtime-library/reference/execve-wexecve.md)|
|[_execlp, _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|[_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|
|[_execlpe, _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|[_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|

Litery na końcu nazwy funkcji określa odmiany.

|_exec — funkcja sufiks|Opis|
|----------------------------|-----------------|
|`e`|`envp`, tablica wskaźników do ustawienia środowiska, jest przekazywany do nowego procesu.|
|`l`|Argumenty wiersza polecenia są przekazywane oddzielnie do `_exec` funkcji. Zazwyczaj używany, gdy liczba parametrów do nowego procesu jest znana z wyprzedzeniem.|
|`p`|`PATH` Zmienna środowiskowa jest używany do znalezienia pliku do wykonania.|
|`v`|`argv`, tablica wskaźników do argumentów wiersza polecenia, jest przekazywany do `_exec`. Zazwyczaj używany, gdy liczba parametrów do nowego procesu jest zmienna.|

## <a name="remarks"></a>Uwagi

Każdy `_exec` funkcji ładuje i uruchamia nowy proces. Wszystkie `_exec` funkcje używają tej samej funkcji systemu operacyjnego ([CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa)). `_exec` Funkcje automatycznie obsługiwać argumenty ciągu znaków wielobajtowych zgodnie z potrzebami, rozpoznawaniu sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową wielobajtowe. `_wexec` Funkcje są wersjami znaków dwubajtowych `_exec` funkcji. `_wexec` Funkcje zachowują się identycznie do ich `_exec` rodziny odpowiedniki z tą różnicą, że mogą nie obsługiwać ciągi znaków wielobajtowych.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_texecl`|`_execl`|`_execl`|`_wexecl`|
|`_texecle`|`_execle`|`_execle`|`_wexecle`|
|`_texeclp`|`_execlp`|`_execlp`|`_wexeclp`|
|`_texeclpe`|`_execlpe`|`_execlpe`|`_wexeclpe`|
|`_texecv`|`_execv`|`_execv`|`_wexecv`|
|`_texecve`|`_execve`|`_execve`|`_wexecve`|
|`_texecvp`|`_execvp`|`_execvp`|`_wexecvp`|
|`_texecvpe`|`_execvpe`|`_execvpe`|`_wexecvpe`|

`cmdname` Parametr określa pliku do wykonania jako nowy proces. Można określić pełną ścieżkę (z katalogu głównego), ścieżka częściowa (od bieżącego katalogu roboczego) lub nazwę pliku. Jeśli `cmdname` nie ma rozszerzenie nazwy pliku lub nie kończą się kropką (.), `_exec` funkcji wyszukiwania dla wskazanego pliku. Jeśli wyszukiwanie zakończy się niepowodzeniem, próbuje taką samą nazwę z rozszerzeniem nazwy pliku .com, a następnie .exe, .bat i rozszerzenia nazw plików .cmd. Jeśli `cmdname` ma rozszerzenie nazwy pliku, tylko to rozszerzenie jest używany w wyszukiwaniu. Jeśli `cmdname` kończy się kropką, `_exec` funkcja wyszukuje `cmdname` bez rozszerzenia nazwy pliku. `_execlp`, `_execlpe`, `_execvp`, i `_execvpe` Wyszukaj `cmdname` (przy użyciu tych samych procedur) w katalogi określone przez `PATH` zmiennej środowiskowej. Jeśli `cmdname` zawiera specyfikator dysku ani żadnych ukośników (to znaczy, jeśli jest ścieżką względną), `_exec` wywołanie przeszukuje tylko dla określonego pliku; nie zostanie przeszukana ścieżka.

Parametry są przekazywane do nowy proces, przekazując co najmniej jednego wskaźnika ciągów znaków jako parametry w `_exec` wywołania. Te ciągi znaków formularza listy parametrów dla nowego procesu. Łączna długość ustawień dziedziczonych środowiska i ciągów znaków tworzących lista parametrów dla nowy proces nie może przekraczać 32 kilobajtów. Kończącego znaku null (\0) dla każdego ciągu nie znajduje się w liczbie, ale są zliczane znaków spacji (wstawiany automatycznie do oddzielania parametrów).

> [!NOTE]
>  Osadzone w ciągach miejsca do magazynowania może spowodować nieoczekiwane zachowanie; na przykład przekazanie `_exec` ciąg `"hi there"` spowoduje w nowym procesie pobierania dwa argumenty `"hi"` i `"there"`. Jeśli celem było zapewnienie nowy proces, otwórz plik o nazwie "Cześć", proces może zakończyć się niepowodzeniem. Można tego uniknąć przez cytowanie ciągu: `"\"hi there\""`.

> [!IMPORTANT]
>  Nie przekazuj dane wejściowe użytkownika do `_exec` jawnie sprawdzeniem jego zawartości. `_exec` spowoduje wywołanie [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) więc pamiętać o tej ścieżce niekwalifikowanych nazw może prowadzić do potencjalnych luk w zabezpieczeniach.

`_exec` Funkcje sprawdzają poprawność swoich parametrów. Oczekiwano, parametry są wskaźniki o wartości null, puste ciągi, czy argument jest pominięty, `_exec` funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają `errno` do `EINVAL` i zwracają wartość -1. Żaden nowy proces jest wykonywany.

Wskaźniki argument mogą być przekazywane jako oddzielne parametry (w `_execl`, `_execle`, `_execlp`, i `_execlpe`) lub jako tablicę wskaźników (w `_execv`, `_execve`, `_execvp`, i `_execvpe`). Co najmniej jeden parametr `arg0`, muszą zostać przekazane do nowego procesu; ten parametr jest `argv`[0] nowego procesu. Zazwyczaj ten parametr jest kopią `cmdname`. (Innej wartości nie generuje błędu).

`_execl`, `_execle`, `_execlp`, I `_execlpe` wywołania są zwykle używane, gdy liczba parametrów jest znana z wyprzedzeniem. Parametr `arg0` jest zazwyczaj wskaźnikiem do `cmdname`. Parametry `arg1` za pośrednictwem `argn` wskaż ciągów znaków tworzących nowe listy parametrów. Wykonaj wskaźnikiem typu null `argn` aby zaznaczyć koniec listy parametrów.

`_execv`, `_execve`, `_execvp`, I `_execvpe` wywołania są pomocne, gdy liczba parametrów do nowego procesu jest zmienna. Wskaźników do parametrów są przekazywane jako tablica, `argv`. Parametr `argv`[0] jest zazwyczaj wskaźnikiem do `cmdname`. Parametry `argv`[1] za pomocą `argv`[`n`] wskaż ciągów znaków tworzących nowe listy parametrów. Parametr `argv`[`n`+ 1] musi być **NULL** wskaźnik, aby zaznaczyć koniec listy parametrów.

Otwórz pliki, które są, kiedy `_exec` zostanie nawiązane połączenie, pozostają otwarte w nowym procesie. W `_execl`, `_execlp`, `_execv`, i `_execvp` wywołań, nowy proces dziedziczy środowisko procesu wywołującego. `_execle`, `_execlpe`, `_execve`, i `_execvpe` wywołania wpływu na środowisko, nowy proces, przekazując listę ustawień środowiska za pomocą `envp` parametru. `envp` Tablica wskaźników znaków każdego elementu (z wyjątkiem ostatnim elementem) wskazuje na ciąg zakończony znakiem null zdefiniować zmienną środowiskową. Taki ciąg ma zwykle postać `NAME` = `value` gdzie `NAME` to nazwa zmiennej środowiskowej i `value` jest wartość ciągu, do którego ustawiono tę zmienną. (Należy pamiętać, że `value` nie jest ujęty w znaki podwójnego cudzysłowu.) Końcowy element `envp` tablicy powinny być **NULL**. Gdy `envp` jest **NULL**, nowy proces dziedziczy ustawienia środowiska procesu wywołującego.

Program wykonywane przy użyciu jednego z `_exec` tak, jakby pole Maksymalna alokacja w nagłówku pliku .exe programu zostały ustawione na wartość domyślną 0xFFFFH funkcji zawsze jest ładowany do pamięci.

`_exec` Wywołania nie zachowuj tryby tłumaczenia otwartych plików. Jeśli nowy proces, należy użyć plików dziedziczone z procesu wywołującego, użyj [_setmode —](../c-runtime-library/reference/setmode.md) procedury, aby ustawić tryb translacji tych plików do żądanego trybu. Należy jawnie opróżniania (przy użyciu `fflush` lub `_flushall`) lub zamknąć dowolny strumień przed `_exec` wywołania funkcji. Ustawienia sygnału nie są zachowywane w nowych procesów, które są tworzone przez wywołania `_exec` procedury. Ustawienia sygnału są resetowane do wartości domyślnych w nowym procesie.

## <a name="example"></a>Przykład

```
// crt_args.c
// Illustrates the following variables used for accessing
// command-line arguments and environment variables:
// argc  argv  envp
// This program will be executed by crt_exec which follows.

#include <stdio.h>

int main( int argc,  // Number of strings in array argv
char *argv[],       // Array of command-line argument strings
char **envp )       // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    printf( "\nCommand-line arguments:\n" );
    for( count = 0; count < argc; count++ )
        printf( "  argv[%d]   %s\n", count, argv[count] );

    // Display each environment variable.
    printf( "\nEnvironment variables:\n" );
    while( *envp != NULL )
        printf( "  %s\n", *(envp++) );

    return;
}
```

Uruchom następujący program do wykonania Crt_args.exe:

```
// crt_exec.c
// Illustrates the different versions of exec, including
//      _execl          _execle          _execlp          _execlpe
//      _execv          _execve          _execvp          _execvpe
//
// Although CRT_EXEC.C can exec any program, you can verify how
// different versions handle arguments and environment by
// compiling and specifying the sample program CRT_ARGS.C. See
// "_spawn, _wspawn Functions" for examples of the similar spawn
// functions.

#include <stdio.h>
#include <conio.h>
#include <process.h>

char *my_env[] =     // Environment for exec?e
{
   "THIS=environment will be",
   "PASSED=to new process by",
   "the EXEC=functions",
   NULL
};

int main( int ac, char* av[] )
{
   char *args[4];
   int ch;
   if( ac != 3 ){
      fprintf( stderr, "Usage: %s <program> <number (1-8)>\n", av[0] );
      return;
   }

   // Arguments for _execv?
   args[0] = av[1];
   args[1] = "exec??";
   args[2] = "two";
   args[3] = NULL;

   switch( atoi( av[2] ) )
   {
   case 1:
      _execl( av[1], av[1], "_execl", "two", NULL );
      break;
   case 2:
      _execle( av[1], av[1], "_execle", "two", NULL, my_env );
      break;
   case 3:
      _execlp( av[1], av[1], "_execlp", "two", NULL );
      break;
   case 4:
      _execlpe( av[1], av[1], "_execlpe", "two", NULL, my_env );
      break;
   case 5:
      _execv( av[1], args );
      break;
   case 6:
      _execve( av[1], args, my_env );
      break;
   case 7:
      _execvp( av[1], args );
      break;
   case 8:
      _execvpe( av[1], args, my_env );
      break;
   default:
      break;
   }

   // This point is reached only if exec fails.
   printf( "\nProcess was not execed." );
   exit( 0 );
}
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** process.h

## <a name="see-also"></a>Zobacz też

[Procedury kontroli środowiska](../c-runtime-library/process-and-environment-control.md)<br/>
[abort](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_spawn, _wspawn, funkcje](../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)