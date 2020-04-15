---
title: _exec, _wexec — Funkcje
ms.date: 11/04/2016
api_location:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 52c9727db544d8b124b37cc5beae369ae06abe10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351664"
---
# <a name="_exec-_wexec-functions"></a>_exec, _wexec — Funkcje

Każda funkcja w tej rodzinie ładuje i wykonuje nowy proces:

|||
|-|-|
|[_execl, _wexecl](../c-runtime-library/reference/execl-wexecl.md)|[_execv, _wexecv](../c-runtime-library/reference/execv-wexecv.md)|
|[_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)|[_execve, _wexecve](../c-runtime-library/reference/execve-wexecve.md)|
|[_execlp, _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|[_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|
|[_execlpe, _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|[_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|

Litera na końcu nazwy funkcji określa odmianę.

|_exec sufiks funkcji|Opis|
|----------------------------|-----------------|
|`e`|`envp`, tablica wskaźników do ustawień środowiska, jest przekazywana do nowego procesu.|
|`l`|Argumenty wiersza polecenia są `_exec` przekazywane indywidualnie do funkcji. Zazwyczaj używane, gdy liczba parametrów do nowego procesu jest znana z wyprzedzeniem.|
|`p`|`PATH`zmienna środowiskowa służy do znajdowania pliku do wykonania.|
|`v`|`argv`, tablica wskaźników do argumentów wiersza `_exec`polecenia jest przekazywana do . Zazwyczaj używane, gdy liczba parametrów do nowego procesu jest zmienna.|

## <a name="remarks"></a>Uwagi

Każda `_exec` funkcja ładuje i wykonuje nowy proces. Wszystkie `_exec` funkcje korzystają z tej samej funkcji systemu operacyjnego ([CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw)). Funkcje `_exec` automatycznie obsługują argumenty ciągów wielobajtowych, rozpoznając sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową wielobajtową. Funkcje `_wexec` są szerokoznakowymi `_exec` wersjami funkcji. Funkcje `_wexec` zachowują się `_exec` identycznie jak ich odpowiedniki rodziny, z tą różnicą, że nie obsługują ciągów znaków wielobajtowych.

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

Parametr `cmdname` określa plik, który ma zostać wykonany jako nowy proces. Można określić pełną ścieżkę (z katalogu głównego), ścieżkę częściową (z bieżącego katalogu roboczego) lub nazwę pliku. Jeśli `cmdname` nie ma rozszerzenia nazwy pliku lub nie kończy się `_exec` kropka (.), funkcja wyszukuje nazwany plik. Jeśli wyszukiwanie nie powiedzie się, próbuje tę samą nazwę podstawową z rozszerzeniem nazwy pliku .com, a następnie z rozszerzeniami nazw plików .exe, .bat i .cmd. Jeśli `cmdname` ma rozszerzenie nazwy pliku, tylko to rozszerzenie jest używane w wyszukiwaniu. Jeśli `cmdname` kończy się kropka, `cmdname` funkcja wyszukuje `_exec` bez rozszerzenia nazwy pliku. `_execlp`, `_execlpe` `_execvp`i `_execvpe` wyszukaj `cmdname` (przy użyciu tych samych `PATH` procedur) w katalogach określonych przez zmienną środowiskową. Jeśli `cmdname` zawiera specyfikator dysku lub żadnych ukośników (to jest, jeśli jest to ścieżka względna), `_exec` wywołanie wyszukuje tylko określony plik; ścieżka nie jest przeszukiwana.

Parametry są przekazywane do nowego procesu, dając jeden lub więcej wskaźników `_exec` do ciągów znaków jako parametry w wywołaniu. Te ciągi znaków tworzą listę parametrów dla nowego procesu. Łączna długość ustawień dziedziczonego środowiska i ciągów tworzących listę parametrów dla nowego procesu nie może przekraczać 32 kilobajtów. Kończący się znak null ("\0") dla każdego ciągu nie jest uwzględniony w liczbie, ale znaki spacji (wstawiane automatycznie w celu oddzielenia parametrów) są zliczane.

> [!NOTE]
> Spacje osadzone w ciągach mogą powodować nieoczekiwane zachowanie; na przykład `_exec` przekazanie `"hi there"` ciągu spowoduje, że nowy proces `"hi"` `"there"`otrzyma dwa argumenty i . Jeśli intencją było, aby nowy proces otworzył plik o nazwie "hi there", proces zakończy się niepowodzeniem. Można tego uniknąć, cytując ciąg: `"\"hi there\""`.

> [!IMPORTANT]
> Nie należy przekazywać `_exec` danych wejściowych użytkownika bez jawnego sprawdzania jego zawartości. `_exec`spowoduje wywołanie [CreateProcess,](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) więc należy pamiętać, że nazwy ścieżek bez zastrzeżeń może prowadzić do potencjalnych luk w zabezpieczeniach.

Funkcje `_exec` sprawdzają ich parametry. Jeśli oczekiwane parametry są wskaźnikami null, pustymi `_exec` ciągami lub pominiętymi, funkcje wywołują nieprawidłowy program obsługi parametrów zgodnie z opisem w [obszarze Sprawdzanie poprawności parametrów.](../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te `errno` funkcje ustawione na i zwraca -1. `EINVAL` Żaden nowy proces nie jest wykonywany.

Wskaźniki argumentów mogą być przekazywane jako `_execl` `_execle`oddzielne `_execlp`parametry `_execlpe`(w , , , `_execv`i `_execve` `_execvp`) `_execvpe`lub jako tablica wskaźników (w , , , i ). Co najmniej jeden `arg0`parametr, musi być przekazany do nowego procesu; ten parametr `argv`jest [0] nowego procesu. Zazwyczaj ten parametr jest `cmdname`kopią pliku . (Inna wartość nie powoduje błędu).

, `_execl` `_execle`, `_execlp`i `_execlpe` wywołania są zwykle używane, gdy liczba parametrów jest znana z wyprzedzeniem. Parametr `arg0` jest zwykle wskaźnikiem do `cmdname`. Parametry `arg1` za `argn` pośrednictwem wskazują ciągi znaków tworzące nową listę parametrów. Wskaźnik zerowy `argn` musi być następowy, aby oznaczyć koniec listy parametrów.

, `_execv` `_execve`, `_execvp`i `_execvpe` wywołania są przydatne, gdy liczba parametrów do nowego procesu jest zmienna. Wskaźniki do parametrów są przekazywane `argv`jako tablica, . Parametr `argv`[0] jest zwykle `cmdname`wskaźnikiem do . Parametry `argv`[1] `argv`przez`n`[ ] wskazują ciągi znaków tworzące nową listę parametrów. Parametr `argv`[`n`+1] musi być wskaźnikiem **NULL,** aby oznaczyć koniec listy parametrów.

Pliki, które są `_exec` otwarte po wywołaniu pozostają otwarte w nowym procesie. W `_execl` `_execlp`, `_execv`, `_execvp` i wywołania, nowy proces dziedziczy środowisko procesu wywołującego. `_execle`, `_execlpe` `_execve`, `_execvpe` i wywołania zmienić środowisko dla nowego procesu, `envp` przekazując listę ustawień środowiska za pośrednictwem parametru. `envp`jest tablicą wskaźników znaków, z których każdy element (z wyjątkiem elementu końcowego) wskazuje ciąg zakończony z wartością null definiujący zmienną środowiskową. Taki ciąg zwykle ma `NAME` = `value` `NAME` formularz, w którym jest `value` nazwa zmiennej środowiskowej i jest wartością ciągu, do której ustawiona jest ta zmienna. (Uwaga, `value` która nie jest ujęta w cudzysłów podwójnych). Ostatnim elementem `envp` tablicy powinien być **NULL**. Gdy `envp` sam jest **NULL**, nowy proces dziedziczy ustawienia środowiska procesu wywołującego.

Program wykonywany z jedną `_exec` z funkcji jest zawsze ładowany do pamięci tak, jakby maksymalne pole alokacji w nagłówku pliku .exe programu zostało ustawione na wartość domyślną 0xFFFFH.

Wywołania `_exec` nie zachowują trybów tłumaczenia otwartych plików. Jeśli nowy proces musi używać plików dziedziczonych z procesu wywołującego, użyj [procedury _setmode,](../c-runtime-library/reference/setmode.md) aby ustawić tryb tłumaczenia tych plików w żądanym trybie. Należy jawnie opróżnić `fflush` `_flushall`(przy użyciu lub) `_exec` lub zamknąć dowolny strumień przed wywołaniem funkcji. Ustawienia sygnału nie są zachowywane w `_exec` nowych procesach, które są tworzone przez wywołania procedur. Ustawienia sygnału są resetowane do ustawień domyślnych w nowym procesie.

## <a name="example"></a>Przykład

```c
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

Uruchom następujący program, aby wykonać Crt_args.exe:

```c
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

[Kontrola procesu i środowiska](../c-runtime-library/process-and-environment-control.md)<br/>
[Przerwać](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_spawn, _wspawn, funkcje](../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)
