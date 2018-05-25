---
title: _execwexec — funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 728c4878736d2e0cafc94660db3d9a709f87715f
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="exec-wexec-functions"></a>_exec, _wexec — Funkcje
Każda funkcja w tej rodzinie ładuje i wykonuje nowy proces:  
  
|||  
|-|-|  
|[_execl, _wexecl](../c-runtime-library/reference/execl-wexecl.md)|[_execv, _wexecv](../c-runtime-library/reference/execv-wexecv.md)|  
|[_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)|[_execve, _wexecve](../c-runtime-library/reference/execve-wexecve.md)|  
|[_execlp, _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|[_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|  
|[_execlpe, _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|[_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|  
  
 Litery na końcu nazwy funkcji określa odmiany.  
  
|_exec — funkcja sufiks|Opis|  
|----------------------------|-----------------|  
|`e`|`envp`, tablicy wskaźników do ustawienia środowiska, są przekazywane do nowego procesu.|  
|`l`|Argumenty wiersza polecenia są przekazywane indywidualnie do `_exec` funkcji. Zazwyczaj używany, gdy liczba parametrów do nowego procesu jest znany wcześniej.|  
|`p`|`PATH` Zmienna środowiskowa służy do znajdowania plików do wykonania.|  
|`v`|`argv`, tablicy wskaźników do argumentów wiersza polecenia, są przekazywane do `_exec`. Zazwyczaj używany, gdy liczba parametrów do nowego procesu jest zmienna.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy `_exec` funkcja ładuje i wykonuje nowego procesu. Wszystkie `_exec` funkcje używają tej samej funkcji systemu operacyjnego ([CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425.aspx)). `_exec` Funkcje obsługi automatycznie argumentów ciągów znaków wielobajtowych zgodnie z potrzebami, rozpoznawanie wielobajtowych sekwencji znaków zgodnie ze strony kodowe wielobajtowe obecnie w użyciu. `_wexec` Funkcje są wersje znaków dwubajtowych `_exec` funkcji. `_wexec` Funkcje zachowują się tak samo ich `_exec` rodziny odpowiedników z tą różnicą, że nie obsługują ciągi znaków wielobajtowych.  
  
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
  
 `cmdname` Parametr określa plik do wykonania jako nowy proces. Można go określić pełną ścieżkę (z katalogu głównego), ścieżka częściowa (z bieżącego katalogu roboczego) lub nazwę pliku. Jeśli `cmdname` nie ma rozszerzenie nazwy pliku lub nie kończą się kropką (.), `_exec` funkcji wyszukiwania dla wskazanego pliku. Jeśli wyszukiwanie nie powiedzie się, próbuje takiej samej nazwie podstawowej z rozszerzeniem nazwy pliku .com, a następnie .exe, bat i cmd rozszerzeniami. Jeśli `cmdname` ma rozszerzenie nazwy pliku tylko tego rozszerzenia jest używany podczas wyszukiwania. Jeśli `cmdname` kończy się kropką, `_exec` funkcja wyszukuje `cmdname` bez rozszerzenia nazwy pliku. `_execlp`, `_execlpe`, `_execvp`, i `_execvpe` Wyszukaj `cmdname` (przy użyciu tych samych procedur) w określonym przez `PATH` zmiennej środowiskowej. Jeśli `cmdname` zawiera specyfikator dysku lub dowolnego ukośniki (jeśli jest ścieżką względną), `_exec` wywołania wyszukuje tylko dla określonego pliku; ścieżka nie jest przeszukiwany.  
  
 Parametry są przekazywane do nowego procesu, zapewniając co najmniej jednego wskaźnika ciągi znaków jako parametry w `_exec` wywołania. Te ciągi znaków tworzą lista parametrów dla nowego procesu. Łączna długość ustawienia dziedziczone środowiska i ciągi tworzące lista parametrów dla nowego procesu nie może przekraczać 32 kilobajtów. Znak końcowy null ('\0') dla każdego ciągu nie jest uwzględnione w liczbie, ale są zliczane znaków spacji (automatycznie wstawione do rozdzielenia parametrów).  
  
> [!NOTE]
>  Spacji osadzonych w ciągach może spowodować nieoczekiwane zachowanie; na przykład przekazywanie `_exec` ciąg `"hi there"` spowoduje nowego procesu pobierania dwa argumenty `"hi"` i `"there"`. Jeśli celem ma nowy proces, otwórz plik o nazwie "Cześć", proces nie powiedzie się. Można tego uniknąć przez zamykający ciąg: `"\"hi there\""`.  
  
> [!IMPORTANT]
>  Nie przekazuj danych wejściowych użytkownika na `_exec` bez jawnie sprawdzania jego zawartości. `_exec` spowoduje wywołanie [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425.aspx) tak należy pamiętać, że ścieżka niekwalifikowanych nazw może prowadzić do potencjalnych luk w zabezpieczeniach.  
  
 `_exec` Funkcje walidację ich parametrów. Jeśli oczekiwane parametry są wskaźniki o wartości null, puste ciągi, lub jest pominięty, `_exec` funkcji Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwróć -1. Żaden nowy proces jest wykonywany.  
  
 Wskaźniki argument mogą być przekazywane jako parametry oddzielne (w `_execl`, `_execle`, `_execlp`, i `_execlpe`) lub w postaci tablicy wskaźników (w `_execv`, `_execve`, `_execvp`, i `_execvpe`). Co najmniej jeden parametr `arg0`, muszą być przekazywane do nowego procesu; ten parametr jest `argv`[0] nowego procesu. Ten parametr jest zazwyczaj, kopię `cmdname`. (Inną wartością nie generuje błędu).  
  
 `_execl`, `_execle`, `_execlp`, I `_execlpe` wywołania są zazwyczaj używane, gdy liczba parametrów jest znany wcześniej. Parametr `arg0` zazwyczaj jest to wskaźnik do `cmdname`. Parametry `arg1` za pośrednictwem `argn` wskaż ciągi znaków tworzących nowe listy parametrów. Wykonaj pustego wskaźnika `argn` można oznaczyć końca listy parametrów.  
  
 `_execv`, `_execve`, `_execvp`, I `_execvpe` wywołania są pomocne, gdy liczba parametrów do nowego procesu jest zmienna. Wskaźniki do parametrów są przekazywane jako tablica `argv`. Parametr `argv`[0] jest zwykle wskaźnik do `cmdname`. Parametry `argv`[1] za pomocą `argv`[`n`] wskaż ciągi znaków tworzących nowe listy parametrów. Parametr `argv`[`n`+ 1] musi być **NULL** wskaźnika można oznaczyć końca listy parametrów.  
  
 Otwórz pliki, które są, kiedy `_exec` wywołanie pozostają otwarte w nowym procesie. W `_execl`, `_execlp`, `_execv`, i `_execvp` wywołań, nowy proces dziedziczy środowisko procesu wywołującego. `_execle`, `_execlpe`, `_execve`, i `_execvpe` wywołania wpływu na środowisko nowy proces, przekazując listę ustawień środowiska za pośrednictwem `envp` parametru. `envp` tablicy wskaźników znak każdego elementu (z wyjątkiem ostatniego elementu) wskazuje ciąg znaków zakończony znakiem null, jest zdefiniowanie zmiennej środowiskowej. Taki ciąg ma zazwyczaj postać `NAME` = `value` gdzie `NAME` to nazwa zmiennej środowiskowej i `value` jest wartość ciągu, do którego jest wartość tej zmiennej. (Należy pamiętać, że `value` nie jest ujęta w znaki podwójnego cudzysłowu.) Końcowy element `envp` tablicy powinna być **NULL**. Gdy `envp` jest **NULL**, nowy proces dziedziczy ustawienia środowiska procesu wywołującego.  
  
 Program wykonać jeden z `_exec` tak, jakby maksymalna alokacja pole w nagłówku pliku .exe programu ustawiono wartość domyślną 0xFFFFH funkcji zawsze jest ładowany do pamięci.  
  
 `_exec` Wywołania nie zachowuj tryby tłumaczenia otwartych plików. Jeśli nowy proces, należy użyć plików dziedziczone z procesu wywołującego, użyj [_setmode —](../c-runtime-library/reference/setmode.md) procedury, aby ustawić tryb tłumaczenia tych plików na żądany tryb. Należy jawnie opróżnić (przy użyciu `fflush` lub `_flushall`) lub zamknąć dowolny strumień przed `_exec` wywołania funkcji. Sygnał ustawienia nie są zachowywane w nowych procesów, które zostały utworzone przy użyciu wywołania `_exec` procedury. Wartość domyślna w nowym procesie zostaną przywrócone ustawienia sygnału.  
  
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
 [Proces i kontroli środowiska](../c-runtime-library/process-and-environment-control.md)   
 [Przerwania](../c-runtime-library/reference/abort.md)   
 [atexit —](../c-runtime-library/reference/atexit.md)   
 [exit, _exit — _exit —](../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit —, _onexit_m —](../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn, _wspawn — funkcje](../c-runtime-library/spawn-wspawn-functions.md)   
 [system, _wsystem](../c-runtime-library/reference/system-wsystem.md)