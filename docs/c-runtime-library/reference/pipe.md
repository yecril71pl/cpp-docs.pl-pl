---
title: "_pipe — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- pipes, creating
- _pipe function
- pipes
- pipe function
ms.assetid: 8d3e9800-4041-44b5-9e93-2df0b0354a75
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 95169aa5070493be76db6306f4d5863d6a2e654f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="pipe"></a>_pipe
Tworzy potoku do odczytu i zapisu.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _pipe(  
   int *pfds,  
   unsigned int psize,  
   int textmode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfds`[2]  
 Tablica do przechowywania odczytu i zapisu deskryptorów plików.  
  
 `psize`  
 Ilość pamięci do zarezerwowania.  
  
 `textmode`  
 Tryb pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość 0 w przypadku powodzenia. Zwraca wartość -1, jeśli wystąpił błąd. W przypadku błędu `errno` ustawiono na jedną z następujących wartości:  
  
-   `EMFILE`, co oznacza, że nie są dostępne nie więcej deskryptorów plików.  
  
-   `ENFILE`, co oznacza przepełnienie tabeli w przypadku plików systemowej.  
  
-   `EINVAL`, co oznacza, że każda tablicy `pfds` jest pusty wskaźnik lub nieprawidłowa wartość `textmode` została przekazana.  
  
 Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `_pipe` Funkcja tworzy *potoku*, która jest sztuczne kanał We/Wy, która jest używana do przekazywania informacji do innych programów. Potok podobny pliku, ponieważ ma ona wskaźnika pliku i/lub deskryptorów plików, a można odczytywane lub zapisywane przy użyciu biblioteki standardowej wejściowe i wyjściowe funkcji. Jednak potoku nie reprezentuje określonego pliku lub urządzenia. Zamiast tego reprezentuje tymczasowego przechowywania w pamięci, która jest niezależna od pamięci tego programu i jest kontrolowany wyłącznie przez system operacyjny.  
  
 `_pipe` podobny `_open` , ale otwiera potoku do odczytywania i zapisywania i zwraca deskryptorów zamiast jedną dwóch plików. Program można użyć obu stronach potoku lub ten, który nie należy go zamknąć. Na przykład procesora poleceń w systemie Windows tworzy potoku podczas wykonywania polecenia takie jak `PROGRAM1 | PROGRAM2`.  
  
 Standardowe dane wyjściowe deskryptor `PROGRAM1` jest dołączony do potoku zapisu deskryptora. Standardowa wejściowy deskryptor `PROGRAM2` jest dołączony do deskryptora odczytu z potoku. Eliminuje to konieczności tworzenia plików tymczasowych do przekazywania informacji do innych programów.  
  
 `_pipe` Funkcja zwraca dwa deskryptorów plików do potoku `pfds` argumentu. Element `pfds`[0] zawiera deskryptora odczytu, a element `pfds`[1] zawiera deskryptora zapisu. Potok deskryptorów plików są używane w taki sam sposób jak inne deskryptorów plików. (Niskiego poziomu dane wejściowe i dane wyjściowe funkcji `_read` i `_write` można odczytywać i zapisu do potoku.) Aby wykryć warunek zakończenia dla potoku, wyszukaj `_read` żądania, która zwraca wartość 0 jako liczba bajtów odczytanych.  
  
 `psize` Argument określa ilość pamięci w bajtach, aby go zarezerwować dla potoku. `textmode` Argument określa tryb tłumaczenia dla potoku. Stała manifestu `_O_TEXT` Określa tłumaczenie tekstu i stałą `_O_BINARY` określa translację binarnego. (Zobacz [fopen —, _wfopen —](../../c-runtime-library/reference/fopen-wfopen.md) opis tryby binarnego i tekstu.) Jeśli `textmode` argument ma wartość 0, `_pipe` używa domyślny tryb tłumaczenia określonej przez zmienną domyślny tryb [_fmode —](../../c-runtime-library/fmode.md).  
  
 W programów wielowątkowych blokowania nie jest wykonywane. Deskryptorów plików, które są zwracane nowo są otwarte i nie powinien być odwołuje się którymkolwiek wątku dopiero po `_pipe` wywołania została ukończona.  
  
 Aby użyć `_pipe` działać do komunikacji między procesem nadrzędny i procesu podrzędnego, każdy proces musi mieć tylko jeden deskryptor Otwórz w potoku. Deskryptory musi być opposites: Jeśli element nadrzędny ma Otwórz deskryptor odczytu, a następnie obiekt podrzędny musi mieć Otwórz deskryptor zapisu. Najprostszym sposobem, w tym celu jest `OR` (`|`) `_O_NOINHERIT` flaga z `textmode`. Następnie należy użyć `_dup` lub `_dup2` do utworzenia dziedziczne kopię deskryptora potok, który chcesz przekazać do elementu podrzędnego. Zamknij deskryptora oryginalny, a następnie zduplikować procesu podrzędnego. Na zwrócenie z wywołania duplikowanie, zamknij deskryptor zduplikowanego procesu nadrzędnego. Aby uzyskać więcej informacji zobacz przykład 2 w dalszej części tego artykułu.  
  
 W systemie operacyjnym Windows potoku jest niszczony, kiedy wszystkie jej deskryptorów zostały zamknięte. (Jeśli zostały zamknięte wszystkie deskryptory odczytu dla potoku, następnie zapisu do potoku powoduje błąd). Wszystkie operacje odczytu i zapisu w potoku czas oczekiwania do czasu brak wystarczającej ilości danych lub za mało miejsca w buforze żądania We/Wy.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_pipe`|\<io.h>|\<fcntl.h>,1 \<errno.h>2|  
  
 1 dla `_O_BINARY` i `_O_TEXT` definicje.  
  
 2 `errno` definicje.  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
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
 To jest aplikacją filtru podstawowego. Go spowoduje utworzenie crt_pipe_beeper aplikacji po utworzeniu potoku kierujący stdout zduplikowanego aplikacji do filtru. Filtr usuwa znaki ASCII 7 (dźwięk).  
  
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
  
 Filtr rzeczywistej aplikacji:  
  
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
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)