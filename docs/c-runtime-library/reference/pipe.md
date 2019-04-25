---
title: _pipe
ms.date: 11/04/2016
apiname:
- _pipe
apilocation:
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
apitype: DLLExport
f1_keywords:
- pipe
- _pipe
helpviewer_keywords:
- pipes, creating
- _pipe function
- pipes
- pipe function
ms.assetid: 8d3e9800-4041-44b5-9e93-2df0b0354a75
ms.openlocfilehash: c5db59fecd84ae291e5651b1cec1be31c815e53a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155976"
---
# <a name="pipe"></a>_pipe

Tworzy potok do odczytu i zapisu.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Wskaźnik do tablicy dwóch **int** do przechowywania odczytu i zapisu deskryptorów plików.

*psize*<br/>
Ilość pamięci do zarezerwowania.

*Tryb tekstowy*<br/>
Tryb pliku.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli kończy się pomyślnie. Zwraca wartość -1, aby wskazać błąd. W przypadku błędu **errno** jest ustawiony na jedną z następujących wartości:

- **EMFILE**, co oznacza, że więcej deskryptorów plików nie są dostępne.

- **ENFILE**, która wskazuje przepełnienie tabeli plików systemu.

- **EINVAL**, który wskazuje, że tablica *dot* jest pustym wskaźnikiem lub nieprawidłową wartością dla *Tryb tekstowy* została przekazana.

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Pipe —** funkcja tworzy *potoku*, który jest sztucznym kanałem we/wy, którego program używa do przekazania informacji do innych programów. Potok przypomina plik, ponieważ ma wskaźnik pliku, deskryptor pliku lub oba, i może być odczytywany lub zapisywany za pomocą standardowej biblioteki danych wejściowych i wyjściowych funkcji. Jednakże potok nie reprezentuje określonego pliku lub urządzenia. Zamiast tego reprezentuje tymczasowy magazyn w pamięci, która jest niezależna od pamięci tego programu i jest całkowicie kontrolowana przez system operacyjny.

**_pipe —** przypomina **_otwórz** , ale otwiera potok do odczytu i zapisu i zwraca dwa deskryptory pliku zamiast jednego. Program może użyć obu stron potoku lub zamknąć tę, której nie potrzebuje. Na przykład procesor poleceń w Windows tworzy potok, kiedy wykonuje polecenia takie jak **PROGRAM1** | **PROGRAM2**.

Standardowe wyjście deskryptora **PROGRAM1** jest dołączone do deskryptora wpisu potoku. Standardowe wejściowy deskryptora **PROGRAM2** jest dołączone do deskryptora odczytu potoku. Eliminuje to potrzebę tworzenia tymczasowych plików do przekazania informacji do innych programów.

**_Pipe —** funkcja zwraca dwa deskryptory plików do potoku *dot* argumentu. Element *dot*[0] zawiera deskryptor odczytu, a element *dot*[1] zawiera deskryptor zapisu. Deskryptory rury są używane w taki sam sposób jak inne deskryptory plików. (Niskiego poziomu wejście i wyjście funkcji **_przeczytaj** i **_write** może odczytywać i zapisywać do potoku.) Aby wykryć warunek-potok, sprawdź **_przeczytaj** żądanie, które zwraca wartość 0 jako liczbę odczytanych bajtów.

*Psize* argument określa ilość pamięci w bajtach, do zarezerwowania dla potoku. *Tryb tekstowy* argument określa tryb translacji dla potoku. Stała manifestu **_O_TEXT** Określa tłumaczenie tekstu i stałą **_O_BINARY** Określa tłumaczenie binarne. (Zobacz [fopen —, _wfopen —](fopen-wfopen.md) opisu trybów tekstowych i binarnych.) Jeśli *Tryb tekstowy* argument ma wartość 0, **_pipe —** wykorzystuje domyślny tryb translacji, który jest określony przez zmienną trybu domyślnego [_fmode](../../c-runtime-library/fmode.md).

W przypadku programów wielowątkowych blokowanie nie jest wykonywane. Deskryptory plików, które są zwracane są otwarte i nie powinny być przywoływane przez żadnych wątków, aż po **_pipe —** wywołanie zostało zakończone.

Aby użyć **_pipe —** funkcji do komunikowania się między procesem nadrzędnym a proces podrzędny, każdy proces musi mieć tylko jeden deskryptor otwarty na rurze. Deskryptory muszą być przeciwieństwem: Jeśli element nadrzędny ma deskryptor odczytu Otwórz, a następnie element podrzędny musi mieć deskryptor zapisu, Otwórz. W tym celu najłatwiej do bitowego lub (**|**) **_O_NOINHERIT** flaga z *Tryb tekstowy*. Następnie należy użyć **_dup —** lub **_dup2 —** utworzyć dziedziczne kopię deskryptora potoku, który chcesz przekazać do elementu podrzędnego. Zamknij oryginalny deskryptor, a następnie powiększ liczbę procesów podrzędnych. Po powrocie z wielokrotnego wywołania, zamknij deskryptora duplikatów w procesie nadrzędnym. Aby uzyskać więcej informacji zobacz przykład 2 w dalszej części tego artykułu.

W systemie operacyjnym Windows potok jest niszczony, kiedy wszystkie jego deskryptory zostały zamknięte. (Jeśli wszystkie deskryptory odczytu potoku zostały zamknięte, następnie zapis do potoku powoduje błąd). Wszystkie operacje odczytu i zapisu na potoku oczekują, dopóki nie ma wystarczającej ilości danych lub wystarczająca przestrzeń w buforze do wykonania żądania We/Wy.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_pipe**|\<io.h>|\<fcntl.h>,1 \<errno.h>2|

1 dla **_O_BINARY** i **_O_TEXT** definicje.

2 **errno** definicje.

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

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

Jest to aplikacja podstawowa filtru. Jego niczego aplikację crt_pipe_beeper po utworzeniu potoku, który kieruje kierującego wskaźnik stdout do bieżącego filtra. Ten filtr usuwa znaki ASCII 7 (beep).

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

Rzeczywiste zastosowanie filtru:

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

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
