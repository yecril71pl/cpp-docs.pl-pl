---
title: _popen, _wpopen
description: Odwołanie do funkcji _popen biblioteki środowiska wykonawczego Microsoft _wpopenC (CRT) i .
ms.date: 4/2/2020
api_name:
- _popen
- _wpopen
- _o__popen
- _o__wpopen
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tpopen
- popen
- wpopen
- _popen
- _wpopen
- _tpopen
helpviewer_keywords:
- tpopen function
- pipes, creating
- _popen function
- _tpopen function
- popen function
- wpopen function
- _wpopen function
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
no-loc:
- _popen
- _wpopen
- _tpopen
- _doserrno
- errno
- _sys_errlist
- _sys_nerr
- EINVAL
ms.openlocfilehash: 5b478893ef8f201f39cb63ecfc7ab174d16b86de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338515"
---
# <a name="_popen-_wpopen"></a>_popen, _wpopen

Tworzy potok i wykonuje polecenie.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
FILE *_popen(
    const char *command,
    const char *mode
);
FILE *_wpopen(
    const wchar_t *command,
    const wchar_t *mode
);
```

### <a name="parameters"></a>Parametry

*Polecenia*\
Polecenie do wykonania.

*Tryb*\
Tryb zwracanego strumienia.

## <a name="return-value"></a>Wartość zwracana

Zwraca strumień skojarzony z jednym końcem utworzonego potoku. Drugi koniec potoku jest skojarzony ze standardowym wejściem lub wyjściem standardowym polecenia zrodzonego. Funkcje zwracają **wartość NULL** po błędzie. Jeśli błąd jest spowodowany przez nieprawidłowy parametr, **errno** jest ustawiony na **EINVAL**. Zobacz uwagi sekcji prawidłowe tryby.

Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_popen** tworzy potok. Następnie asynchronicznie wykonuje zduplikowane kopie procesora poleceń i używa *polecenia* jako wiersza polecenia. *Tryb* ciągu znaków określa typ żądanego dostępu w następujący sposób.

|Tryb dostępu|Opis|
|-|-|
|**"r"**|Proces wywołujący może odczytać standardowe dane wyjściowe polecenia zrodzone przy użyciu zwracany strumień.|
|**"w"**|Proces wywoływania można zapisać do zduplikowanego polecenia standardowe dane wejściowe przy użyciu zwracany strumień.|
|**"b"**|Otwórz w trybie binarnym.|
|**"t"**|Otwórz w trybie tekstowym.|

> [!NOTE]
> Jeśli jest używana w programie systemu Windows, funkcja **_popen** zwraca nieprawidłowy wskaźnik pliku, który powoduje, że program przestaje odpowiadać przez czas nieokreślony. **_popen** działa poprawnie w aplikacji konsoli. Aby utworzyć aplikację systemu Windows, która przekierowuje dane wejściowe i wyjściowe, zobacz [Tworzenie procesu podrzędnego z przekierowanym wejściem i wyjściem](/windows/win32/ProcThread/creating-a-child-process-with-redirected-input-and-output) w usłudze Windows SDK.

**_wpopen** jest szerokoznakową wersją **_popen**; argument *path* do **_wpopen** jest ciągiem znaków o szerokim charakterze. **_wpopen** i **_popen** zachowują się identycznie w przeciwnym razie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_popen**|\<stdio.h>|
|**_wpopen**|\<stdio.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_popen.c
/* This program uses _popen and _pclose to receive a
* stream of text from a system process.
*/

#include <stdio.h>
#include <stdlib.h>

int main( void )
{

   char   psBuffer[128];
   FILE   *pPipe;

        /* Run DIR so that it writes its output to a pipe. Open this
         * pipe with read text attribute so that we can read it
         * like a text file.
         */

   if( (pPipe = _popen( "dir *.c /on /p", "rt" )) == NULL )
      exit( 1 );

   /* Read pipe until end of file, or an error occurs. */

   while(fgets(psBuffer, 128, pPipe))
   {
      puts(psBuffer);
   }

   /* Close pipe and print return value of pPipe. */
   if (feof( pPipe))
   {
     printf( "\nProcess returned %d\n", _pclose( pPipe ) );
   }
   else
   {
     printf( "Error: Failed to read the pipe to the end.\n");
   }
}
```

Ten wynik danych wyjściowych zakłada, że w bieżącym `.c` katalogu znajduje się tylko jeden plik, który ma rozszerzenie nazwy pliku.

```Output
Volume in drive C is CDRIVE
Volume Serial Number is 0E17-1702

Directory of D:\proj\console\test1

07/17/98  07:26p                   780 popen.c
               1 File(s)            780 bytes
                             86,597,632 bytes free

Process returned 0
```

## <a name="see-also"></a>Zobacz też

[Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)\
[_pclose](pclose.md)\
[_pipe](pipe.md)
