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
ms.openlocfilehash: dab670c5baef1c51c39a4c936380fab92c5103cc
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300310"
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
|`e`|`envp`, tablica wskaźników do ustawień środowiska, jest przenoszona do nowego procesu.|
|`l`|Argumenty wiersza polecenia są przesyłane pojedynczo do funkcji `_exec`. Zwykle używany, gdy liczba parametrów nowego procesu jest znana z wyprzedzeniem.|
|`p`|Zmienna środowiskowa `PATH` jest używana do znajdowania pliku do wykonania.|
|`v`|`argv`, tablica wskaźników do argumentów wiersza polecenia, jest przenoszona do `_exec`. Zwykle używany, gdy liczba parametrów nowego procesu jest zmienna.|

## <a name="remarks"></a>Uwagi

Każda funkcja `_exec` ładuje i wykonuje nowy proces. Wszystkie funkcje `_exec` korzystają z tej samej funkcji systemu operacyjnego ([CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw)). Funkcja `_exec` automatycznie obsługuje argumenty ciągu znaków wielobajtowych, a także rozpoznaje sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową. `_wexec` funkcje są wersjami znaków dwubajtowych funkcji `_exec`. `_wexec` funkcje zachowują się identycznie z ich odpowiednikami rodziny `_exec`, z wyjątkiem tego, że nie obsługują ciągów znaków wielobajtowych.

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

`cmdname` parametr określa plik, który ma być wykonywany jako nowy proces. Można określić pełną ścieżkę (z katalogu głównego), ścieżkę częściową (z bieżącego katalogu roboczego) lub nazwę pliku. Jeśli `cmdname` nie ma rozszerzenia nazwy pliku lub nie kończy się kropką (.), funkcja `_exec` wyszukuje nazwany plik. Jeśli wyszukiwanie nie powiedzie się, próbuje ona tę samą nazwę podstawową z rozszerzeniem nazwy pliku. com, a następnie z rozszerzeniami. exe,. bat i. cmd. Jeśli `cmdname` ma rozszerzenie nazwy pliku, w wyszukiwaniu używane jest tylko rozszerzenie. Jeśli `cmdname` kończą się kropką, funkcja `_exec` wyszukuje `cmdname` bez rozszerzenia nazwy pliku. `_execlp`, `_execlpe`, `_execvp`i `_execvpe` wyszukiwanie `cmdname` (przy użyciu tych samych procedur) w katalogach określonych przez zmienną środowiskową `PATH`. Jeśli `cmdname` zawiera specyfikator dysku lub dowolne ukośniki (to oznacza, że jeśli jest ścieżką względną), wywołanie `_exec` wyszukuje tylko określony plik; ścieżka nie jest przeszukiwana.

Parametry są przesyłane do nowego procesu przez nadanie co najmniej jednego wskaźnika do ciągów znaków jako parametrów w wywołaniu `_exec`. Te ciągi znaków tworzą listę parametrów dla nowego procesu. Łączna długość dziedziczonych ustawień środowiska i ciągów tworzących listę parametrów dla nowego procesu nie może przekraczać 32 kilobajtów. Kończący znak null (' \ 0 ') dla każdego ciągu nie jest uwzględniony w liczniku, ale zliczane są znaki spacji (wstawiane automatycznie w celu oddzielenia parametrów).

> [!NOTE]
>  Spacje osadzone w ciągach mogą spowodować nieoczekiwane zachowanie; na przykład przekazywanie `_exec` ciągu `"hi there"` spowoduje powstanie nowego procesu pobierającego dwa argumenty, `"hi"` i `"there"`. Jeśli chcesz, aby nowy proces otworzył plik o nazwie "Witaj tam", proces zakończy się niepowodzeniem. Można to uniknąć przez wyrażenie Quote ciągu: `"\"hi there\""`.

> [!IMPORTANT]
>  Nie przekazuj danych wejściowych użytkownika do `_exec` bez jawnego sprawdzenia jego zawartości. `_exec` spowoduje wywołanie metody [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) , dlatego należy pamiętać, że niekwalifikowane nazwy ścieżek mogą prowadzić do potencjalnych luk w zabezpieczeniach.

Funkcje `_exec` sprawdzają poprawność swoich parametrów. Jeśli oczekiwane parametry mają wskaźniki o wartości null, puste ciągi lub pominięte, funkcje `_exec` wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają `errno` na `EINVAL` i zwracają wartość-1. Żaden nowy proces nie jest wykonywany.

Wskaźniki argumentów mogą być przesyłane jako osobne parametry (w `_execl`, `_execle`, `_execlp`i `_execlpe`) lub jako tablica wskaźników (w `_execv`, `_execve`, `_execvp`i `_execvpe`). Co najmniej jeden parametr, `arg0`, musi zostać przesłany do nowego procesu; Ten parametr jest `argv`[0] nowego procesu. Zazwyczaj ten parametr jest kopią `cmdname`. (Inna wartość nie powoduje błędu).

Wywołania `_execl`, `_execle`, `_execlp`i `_execlpe` są zwykle używane, gdy liczba parametrów jest znana z wyprzedzeniem. Parametr `arg0` jest zwykle wskaźnikiem do `cmdname`. Parametry `arg1` przez `argn` wskazują ciągi znaków tworzące nową listę parametrów. Aby oznaczyć koniec listy parametrów, wskaźnik o wartości null musi następować `argn`.

Wywołania `_execv`, `_execve`, `_execvp`i `_execvpe` są przydatne, gdy liczba parametrów nowego procesu jest zmienna. Wskaźniki do parametrów są przesyłane jako tablica, `argv`. Parametr `argv`[0] jest zwykle wskaźnikiem do `cmdname`. Parametry `argv`[1] do `argv`[`n`] wskazują ciągi znaków tworzące nową listę parametrów. Parametr `argv`[`n`+ 1] musi być **pustym** wskaźnikiem, aby oznaczyć koniec listy parametrów.

Pliki, które są otwarte, gdy zostanie utworzone wywołanie `_exec` w nowym procesie. W `_execl`, `_execlp`, `_execv`i `_execvp` wywołania, nowy proces dziedziczy środowisko procesu wywołującego. wywołania `_execle`, `_execlpe`, `_execve`i `_execvpe` zmieniają środowisko dla nowego procesu przez przekazanie listy ustawień środowiska za pomocą parametru `envp`. `envp` jest tablicą wskaźników znaków, każdy element (z wyjątkiem elementu końcowego) wskazuje ciąg zakończony znakiem null definiujący zmienną środowiskową. Taki ciąg ma zwykle postać `NAME`=`value` gdzie `NAME` jest nazwą zmiennej środowiskowej, a `value` to wartość ciągu, do której ta zmienna jest ustawiona. (Należy zauważyć, że `value` nie jest ujęta w znaki podwójnego cudzysłowu). Końcowy element tablicy `envp` powinien mieć **wartość null**. Gdy sama `envp` ma **wartość null**, nowy proces dziedziczy ustawienia środowiska procesu wywołującego.

Program wykonany przy użyciu jednej z `_exec`ch funkcji jest zawsze ładowany do pamięci, tak jakby pole maksymalnego przydziału w nagłówku pliku exe programu miało ustawioną wartość domyślną 0xFFFFH.

Wywołania `_exec` nie zachowują trybów tłumaczenia otwartych plików. Jeśli nowy proces musi używać plików dziedziczonych z procesu wywołującego, użyj procedury [_setmode](../c-runtime-library/reference/setmode.md) , aby ustawić tryb tłumaczenia tych plików na żądany tryb. Musisz jawnie opróżniać (przy użyciu `fflush` lub `_flushall`) lub zamknąć wszystkie strumienie przed wywołaniem funkcji `_exec`. Ustawienia sygnału nie są zachowywane w nowych procesach, które są tworzone przez wywołania do procedur `_exec`. Ustawienia sygnału są resetowane do ustawień domyślnych w nowym procesie.

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

Uruchom następujący program, aby wykonać Crt_args. exe:

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

**Nagłówek:** Process. h

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../c-runtime-library/process-and-environment-control.md)<br/>
[abort](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_spawn, _wspawn, funkcje](../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)
