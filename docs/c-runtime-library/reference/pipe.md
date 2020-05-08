---
title: _pipe
ms.date: 4/2/2020
api_name:
- _pipe
- _o__pipe
api_location:
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- pipe
- _pipe
helpviewer_keywords:
- pipes, creating
- _pipe function
- pipes
- pipe function
ms.assetid: 8d3e9800-4041-44b5-9e93-2df0b0354a75
ms.openlocfilehash: d3805de6a591169f94926c09a4542ec01f221d1d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916841"
---
# <a name="_pipe"></a>_pipe

Tworzy potok do odczytu i zapisu.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _pipe(
   int *pfds,
   unsigned int psize,
   int textmode
);
```

### <a name="parameters"></a>Parametry

*pfds*<br/>
Wskaźnik do tablicy dwóch liczb **całkowitych** do przechowywania deskryptorów plików odczytu i zapisu.

*psize*<br/>
Ilość pamięci do zarezerwowania.

*TextMode*<br/>
Tryb pliku.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli powodzenie. Zwraca wartość-1, aby wskazać błąd. W przypadku błędu **errno** jest ustawiony na jedną z następujących wartości:

- **EMFILE**, który wskazuje, że nie ma więcej dostępnych deskryptorów plików.

- **Enfile**, który wskazuje przepełnienie tabeli plików systemowych.

- **EINVAL**, która wskazuje, że tablica *pfds* jest wskaźnikiem o wartości null lub że przekazano nieprawidłową wartość typu *TextMode* .

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_pipe** tworzy *potok*, który jest sztucznym kanałem we/wy używanym przez program do przekazywania informacji do innych programów. Potok przypomina plik, ponieważ ma wskaźnik pliku, deskryptor pliku lub oba te elementy, z których może być odczytywany lub zapisywana przy użyciu standardowych funkcji danych wejściowych i wyjściowych biblioteki standardowej. Jednak potok nie reprezentuje określonego pliku lub urządzenia. Zamiast tego reprezentuje magazyn tymczasowy w pamięci, który jest niezależny od własnej pamięci programu i jest kontrolowany w całości przez system operacyjny.

**_pipe** przypomina **_open** , ale otwiera potok do odczytu i zapisu oraz zwraca dwa deskryptory plików zamiast jednego. Program może używać obu stron potoku lub zamknąć ten, którego nie potrzebuje. Na przykład procesor poleceń w systemie Windows tworzy potok, gdy wykonuje polecenie, takie jak **PROGRAM1** | **PROGRAM2**.

Standardowy deskryptor wyjściowy elementu **PROGRAM1** jest dołączony do deskryptora zapisu potoku. Standardowy deskryptor wejścia **PROGRAM2** jest dołączany do deskryptora odczytu potoku. Eliminuje to konieczność tworzenia plików tymczasowych w celu przekazywania informacji do innych programów.

Funkcja **_pipe** zwraca dwa deskryptory plików do potoku w argumencie *pfds* . Element *pfds*[0] zawiera deskryptor odczytu, a element *pfds*[1] zawiera deskryptor zapisu. Deskryptory pliku potoku są używane w taki sam sposób, jak w przypadku innych deskryptorów plików. (Funkcje danych wejściowych i wyjściowych niskiego poziomu **_read** i **_write** mogą odczytywać i zapisywać w potoku). Aby wykryć warunek końca potoku, Wyszukaj żądanie **_read** , które zwraca 0 jako liczbę odczytanych bajtów.

Argument *psize* określa ilość pamięci, w bajtach, do zarezerwowania dla potoku. Argument *TextMode* określa tryb tłumaczenia dla potoku. Stała manifestu **_O_TEXT** określa tłumaczenie tekstu, a stała **_O_BINARY** określa translację binarną. (Zobacz [fopen, _wfopen,](fopen-wfopen.md) Aby uzyskać opis trybów tekstowych i binarnych). Jeśli argument *TextMode* ma wartość 0, **_pipe** używa domyślnego trybu tłumaczenia określonego przez zmienną trybu domyślnego [_fmode](../../c-runtime-library/fmode.md).

W programach wielowątkowych nie jest wykonywane blokowanie. Zwracane deskryptory plików są nowo otwierane i nie powinny odwoływać się do żadnego wątku do momentu zakończenia wywołania **_pipe** .

Aby użyć funkcji **_pipe** do komunikacji między procesem nadrzędnym i procesem podrzędnym, każdy proces musi mieć otwarty tylko jeden deskryptor w potoku. Deskryptory muszą być odwrotne: Jeśli element nadrzędny ma otwarty skrypt odczytu, element podrzędny musi mieć otwarty deskryptor zapisu. Najprostszym sposobem wykonania tej czynności jest bitowe lub (**|**) flagi **_O_NOINHERIT** z *tekstem*. Następnie użyj **_dup** lub **_dup2** , aby utworzyć dziedziczną kopię deskryptora potoku, który ma zostać przekazany do elementu podrzędnego. Zamknij oryginalny deskryptor, a następnie przeduplikuj proces podrzędny. Po powrocie z wywołania duplikatu Zamknij zduplikowany deskryptor w procesie nadrzędnym. Aby uzyskać więcej informacji, zobacz przykład 2 w dalszej części tego artykułu.

W systemie operacyjnym Windows potok jest niszczony, gdy wszystkie jego deskryptory zostały zamknięte. (Jeśli wszystkie deskryptory odczytu w potoku zostały zamknięte, zapis do potoku powoduje wystąpienie błędu). Wszystkie operacje odczytu i zapisu w potoku czekają na wystarczającą ilość danych lub wystarczającą ilość miejsca w buforze, aby zakończyć żądanie we/wy.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_pipe**|\<IO. h>|\<fcntl. h>, 1 \<errno. h>2|

1 dla definicji **_O_BINARY** i **_O_TEXT** .

2 definicje **errno** .

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example-1"></a>Przykład 1

```C
// crt_pipe.c
/* This program uses the _pipe function to pass streams of
* text to spawned processes.
*/

#include <stdlib.h>
#include <stdio.h>
#include <io.h>
#include <fcntl.h>
#include <process.h>
#include <math.h>

enum PIPES { READ, WRITE }; /* Constants 0 and 1 for READ and WRITE */
#define NUMPROBLEM 8

int main( int argc, char *argv[] )
{

   int fdpipe[2];
   char hstr[20];
   int pid, problem, c;
   int termstat;

   /* If no arguments, this is the spawning process */
   if( argc == 1 )
   {

      setvbuf( stdout, NULL, _IONBF, 0 );

      /* Open a set of pipes */
      if( _pipe( fdpipe, 256, O_BINARY ) == -1 )
          exit( 1 );

      /* Convert pipe read descriptor to string and pass as argument
       * to spawned program. Program spawns itself (argv[0]).
       */
      _itoa_s( fdpipe[READ], hstr, sizeof(hstr), 10 );
      if( ( pid = _spawnl( P_NOWAIT, argv[0], argv[0],
            hstr, NULL ) ) == -1 )
          printf( "Spawn failed" );

      /* Put problem in write pipe. Since spawned program is
       * running simultaneously, first solutions may be done
       * before last problem is given.
       */
      for( problem = 1000; problem <= NUMPROBLEM * 1000; problem += 1000)
      {

         printf( "Son, what is the square root of %d?\n", problem );
         _write( fdpipe[WRITE], (char *)&problem, sizeof( int ) );

      }

      /* Wait until spawned program is done processing. */
      _cwait( &termstat, pid, WAIT_CHILD );
      if( termstat & 0x0 )
         printf( "Child failed\n" );

      _close( fdpipe[READ] );
      _close( fdpipe[WRITE] );

   }

   /* If there is an argument, this must be the spawned process. */
   else
   {

      /* Convert passed string descriptor to integer descriptor. */
      fdpipe[READ] = atoi( argv[1] );

      /* Read problem from pipe and calculate solution. */
      for( c = 0; c < NUMPROBLEM; c++ )
      {

        _read( fdpipe[READ], (char *)&problem, sizeof( int ) );
        printf( "Dad, the square root of %d is %3.2f.\n",
                 problem, sqrt( ( double )problem ) );

      }
   }
}
```

```Output
Son, what is the square root of 1000?
Son, what is the square root of 2000?
Son, what iDad, the square root of 1000 is 31.62.
Dad, the square root of 2000 is 44.72.
s the square root of 3000?
Dad, the square root of 3000 is 54.77.
Son, what is the square root of 4000?
Dad, the square root of 4000 is 63.25.
Son, what is the square root of 5000?
Dad, the square root of 5000 is 70.71.
Son, what is the square root of 6000?
SonDad, the square root of 6000 is 77.46.
, what is the square root of 7000?
Dad, the square root of 7000 is 83.67.
Son, what is the square root of 8000?
Dad, the square root of 8000 is 89.44.
```

## <a name="example-2"></a>Przykład 2

Jest to podstawowa aplikacja filtrów. Powoduje ono duplikowanie aplikacji crt_pipe_beeper po utworzeniu potoku, który kieruje do filtru filtr strumienia aplikacji. Filtr usuwa znaki ASCII 7 (sygnał dźwiękowy).

```C
// crt_pipe_beeper.c

#include <stdio.h>
#include <string.h>

int main()
{
   int   i;
   for(i=0;i<10;++i)
      {
         printf("This is speaker beep number %d...\n\7", i+1);
      }
   return 0;
}
```

Rzeczywista aplikacja filtru:

```C
// crt_pipe_BeepFilter.C
// arguments: crt_pipe_beeper.exe

#include <windows.h>
#include <process.h>
#include <memory.h>
#include <string.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>

#define   OUT_BUFF_SIZE 512
#define   READ_FD 0
#define   WRITE_FD 1
#define   BEEP_CHAR 7

char szBuffer[OUT_BUFF_SIZE];

int Filter(char* szBuff, ULONG nSize, int nChar)
{
   char* szPos = szBuff + nSize -1;
   char* szEnd = szPos;
   int nRet = nSize;

   while (szPos > szBuff)
   {
      if (*szPos == nChar)
         {
            memmove(szPos, szPos+1, szEnd - szPos);
            --nRet;
         }
      --szPos;
   }
   return nRet;
}

int main(int argc, char** argv)
{
   int nExitCode = STILL_ACTIVE;
   if (argc >= 2)
   {
      HANDLE hProcess;
      int fdStdOut;
      int fdStdOutPipe[2];

      // Create the pipe
      if(_pipe(fdStdOutPipe, 512, O_NOINHERIT) == -1)
         return   1;

      // Duplicate stdout file descriptor (next line will close original)
      fdStdOut = _dup(_fileno(stdout));

      // Duplicate write end of pipe to stdout file descriptor
      if(_dup2(fdStdOutPipe[WRITE_FD], _fileno(stdout)) != 0)
         return   2;

      // Close original write end of pipe
      _close(fdStdOutPipe[WRITE_FD]);

      // Spawn process
      hProcess = (HANDLE)_spawnvp(P_NOWAIT, argv[1],
       (const char* const*)&argv[1]);

      // Duplicate copy of original stdout back into stdout
      if(_dup2(fdStdOut, _fileno(stdout)) != 0)
         return   3;

      // Close duplicate copy of original stdout
      _close(fdStdOut);

      if(hProcess)
      {
         int nOutRead;
         while   (nExitCode == STILL_ACTIVE)
         {
            nOutRead = _read(fdStdOutPipe[READ_FD],
             szBuffer, OUT_BUFF_SIZE);
            if(nOutRead)
            {
               nOutRead = Filter(szBuffer, nOutRead, BEEP_CHAR);
               fwrite(szBuffer, 1, nOutRead, stdout);
            }

            if(!GetExitCodeProcess(hProcess,(unsigned long*)&nExitCode))
               return 4;
         }
      }
   }
   return nExitCode;
}
```

```Output
This is speaker beep number 1...
This is speaker beep number 2...
This is speaker beep number 3...
This is speaker beep number 4...
This is speaker beep number 5...
This is speaker beep number 6...
This is speaker beep number 7...
This is speaker beep number 8...
This is speaker beep number 9...
This is speaker beep number 10...
```

## <a name="see-also"></a>Zobacz też

[Proces i kontrola środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
