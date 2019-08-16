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
ms.openlocfilehash: d31192a25cce86dad6f8e1e8b0258a457d0a5436
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500136"
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

|sufiks funkcji _exec|Opis|
|----------------------------|-----------------|
|`e`|`envp`Tablica wskaźników do ustawień środowiska jest przenoszona do nowego procesu.|
|`l`|Argumenty wiersza polecenia są przesyłane pojedynczo do `_exec` funkcji. Zwykle używany, gdy liczba parametrów nowego procesu jest znana z wyprzedzeniem.|
|`p`|`PATH`Zmienna środowiskowa służy do znajdowania pliku do wykonania.|
|`v`|`argv`Tablica wskaźników do argumentów wiersza polecenia jest przenoszona do `_exec`. Zwykle używany, gdy liczba parametrów nowego procesu jest zmienna.|

## <a name="remarks"></a>Uwagi

Każda `_exec` funkcja ładuje i wykonuje nowy proces. Wszystkie `_exec` funkcje używają tej samej funkcji systemu operacyjnego ([CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw)). `_exec` Funkcje automatycznie obsługują argumenty ciągu znaków wielobajtowych, aby rozpoznawać sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową. Funkcje są wersjami `_exec` znaków dwubajtowych funkcji. `_wexec` Funkcje zachowują się identycznie ze `_exec` swoimi odpowiednikami rodzin, z tą różnicą, że nie obsługują ciągów znaków wielobajtowych. `_wexec`

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

`cmdname` Parametr określa plik, który ma być wykonywany jako nowy proces. Można określić pełną ścieżkę (z katalogu głównego), ścieżkę częściową (z bieżącego katalogu roboczego) lub nazwę pliku. Jeśli `cmdname` nazwa pliku nie ma rozszerzenia lub nie kończy się kropką (.) `_exec` , funkcja szuka nazwanego pliku. Jeśli wyszukiwanie nie powiedzie się, próbuje ona tę samą nazwę podstawową z rozszerzeniem nazwy pliku. com, a następnie z rozszerzeniami. exe,. bat i. cmd. Jeśli `cmdname` ma rozszerzenie nazwy pliku, tylko to rozszerzenie jest używane w wyszukiwaniu. Jeśli `cmdname` `cmdname` zostanie `_exec` zakończona kropką, funkcja szuka bez rozszerzenia nazwy pliku. `_execlp`, `_execlpe`, `_execvp`i wyszukiwania(`cmdname` przy użyciu tych samych procedur) w katalogach określonych przez zmienną środowiskową. `PATH` `_execvpe` Jeśli `cmdname` zawiera specyfikator dysku lub dowolne ukośniki (to oznacza, że jeśli jest ścieżką względną) `_exec` , wywołanie przeszukuje tylko określony plik; ścieżka nie jest przeszukiwana.

Parametry są przesyłane do nowego procesu przez nadanie co najmniej jednego wskaźnika do ciągów znaków jako parametrów w `_exec` wywołaniu. Te ciągi znaków tworzą listę parametrów dla nowego procesu. Łączna długość dziedziczonych ustawień środowiska i ciągów tworzących listę parametrów dla nowego procesu nie może przekraczać 32 kilobajtów. Kończący znak null (' \ 0 ') dla każdego ciągu nie jest uwzględniony w liczniku, ale zliczane są znaki spacji (wstawiane automatycznie w celu oddzielenia parametrów).

> [!NOTE]
>  Spacje osadzone w ciągach mogą spowodować nieoczekiwane zachowanie; na przykład przekazanie `_exec` ciągu `"hi there"` spowoduje powstanie nowego `"hi"` procesu pobierającego dwa argumenty i `"there"`. Jeśli chcesz, aby nowy proces otworzył plik o nazwie "Witaj tam", proces zakończy się niepowodzeniem. Można to uniknąć przez wyrażenie Quote ciągu: `"\"hi there\""`.

> [!IMPORTANT]
>  Nie przekazuj danych wejściowych użytkownika do `_exec` bez jawnego sprawdzania jego zawartości. `_exec`spowoduje wywołanie metody [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) , dlatego należy pamiętać, że niekwalifikowane nazwy ścieżek mogą prowadzić do potencjalnych luk w zabezpieczeniach.

`_exec` Funkcje sprawdzają poprawność swoich parametrów. Jeśli oczekiwane parametry mają wskaźniki o wartości null, puste ciągi lub pominięte `_exec` , funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają `errno` na `EINVAL` i zwracają wartość-1. Żaden nowy proces nie jest wykonywany.

Wskaźniki argumentów mogą być przesyłane jako osobne parametry (w `_execl` `_execlp`, `_execle`, i `_execvp` `_execlpe`) lub jako tablica wskaźników (w `_execv` `_execve`,, i `_execvpe`). Co najmniej jeden parametr `arg0`,,, musi zostać przesłany do nowego procesu; ten parametr to `argv`[0] nowego procesu. Zazwyczaj ten parametr jest kopią `cmdname`. (Inna wartość nie powoduje błędu).

`_execle` Wywołania,,`_execlp`i są`_execlpe` zwykle używane, gdy liczba parametrów jest znana z wyprzedzeniem. `_execl` Parametr `arg0` jest zwykle wskaźnikiem do `cmdname`. `arg1` Parametry`argn` wskazujące na ciągi znaków tworzące nową listę parametrów. Wskaźnik o wartości null musi `argn` następować po końcu listy parametrów.

`_execve` Wywołania,,`_execvp`i są`_execvpe` przydatne, gdy liczba parametrów nowego procesu jest zmienna. `_execv` Wskaźniki do parametrów są przenoszone jako tablica, `argv`. Parametr `argv`[0] jest zwykle wskaźnikiem do `cmdname`. Parametry `argv`[1] do `argv`[`n`] wskazują ciągi znaków tworzące nową listę parametrów. Parametr `argv`[`n`+ 1] musi być pustym wskaźnikiem, aby można było oznaczyć koniec listy parametrów.

Pliki, które są otwarte, `_exec` gdy nastąpi pozostawanie otwarte w nowym procesie. W `_execl`, `_execlp`, ,`_execv` i`_execvp` wywołania, nowy proces dziedziczy środowisko procesu wywołującego. `_execle`, `_execlpe`, `_execve`, `envp` i `_execvpe` wywołuje zmiany środowiska dla nowego procesu przez przekazanie listy ustawień środowiska za pomocą parametru. `envp`jest tablicą wskaźników znakowych, każdy element (z wyjątkiem elementu końcowego) wskazuje na ciąg zakończony znakiem null definiujący zmienną środowiskową. Taki ciąg ma `NAME` zwykle postać = `value` , gdzie `NAME` jest nazwą zmiennej środowiskowej i `value` jest wartością ciągu, do której ta zmienna jest ustawiona. (Należy zauważyć `value` , że nie jest ujęty w znaki podwójnego cudzysłowu). Końcowy element `envp` tablicy powinien mieć **wartość null**. Gdy `envp` sama ma **wartość null**, nowy proces dziedziczy ustawienia środowiska procesu wywołującego.

Program wykonany przy użyciu jednej z `_exec` funkcji jest zawsze ładowany do pamięci, tak jakby pole maksymalnego przydziału w nagłówku pliku exe programu miało ustawioną wartość domyślną 0xFFFFH.

`_exec` Wywołania nie zachowują trybów tłumaczenia otwartych plików. Jeśli nowy proces musi używać plików dziedziczonych z procesu wywołującego, użyj procedury [_setmode](../c-runtime-library/reference/setmode.md) , aby ustawić tryb tłumaczenia tych plików na żądany tryb. Musisz jawnie opróżniać (przy `fflush` użyciu `_flushall`lub) lub `_exec` zamknąć wszystkie strumienie przed wywołaniem funkcji. Ustawienia sygnału nie są zachowywane w nowych procesach, które są tworzone `_exec` przez wywołania procedur. Ustawienia sygnału są resetowane do ustawień domyślnych w nowym procesie.

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

Uruchom następujący program, aby wykonać Crt_args. exe:

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

**Nagłówek:** Process. h

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../c-runtime-library/process-and-environment-control.md)<br/>
[abort](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_spawn, _wspawn, funkcje](../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)
