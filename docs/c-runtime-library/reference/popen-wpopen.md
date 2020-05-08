---
title: _popen, _wpopen
description: Odwołanie do biblioteki środowiska uruchomieniowego języka Microsoft C (CRT) _popen i _wpopen.
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 37e5bb491234e46a0e3330bc2fd42c16e54793fc
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915289"
---
# <a name="_popen-_wpopen"></a>_popen, _wpopen

Tworzy potok i wykonuje polecenie.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*dotyczące*\
Polecenie do wykonania.

*wyst*\
Tryb zwróconego strumienia.

## <a name="return-value"></a>Wartość zwracana

Zwraca strumień skojarzony z jednym końcem utworzonego potoku. Drugi koniec potoku jest skojarzony ze zduplikowanym wyjściem polecenia lub standardowym danymi wyjściowymi. Funkcje zwracają **wartość null** w przypadku błędu. Jeśli błąd jest spowodowany przez nieprawidłowy parametr, **errno** jest ustawiona na **EINVAL**. Zobacz sekcję Uwagi, aby uzyskać prawidłowe tryby.

Aby uzyskać informacje o tych i innych kodach błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_popen** tworzy potok. Następnie asynchronicznie wykonuje zduplikowaną kopię procesora poleceń i używa *polecenia* jako wiersza polecenia. *Tryb* ciągu znaków określa typ żądanego dostępu w następujący sposób.

|Tryb dostępu|Opis|
|-|-|
|**®**|Proces wywołujący może odczytać standardowe dane wyjściowe polecenia zduplikowanego przy użyciu zwróconego strumienia.|
|**k**|Proces wywołujący może zapisywać do standardowych danych wejściowych polecenia, używając zwróconego strumienia.|
|**b**|Otwórz w trybie binarnym.|
|**&**|Otwórz w trybie tekstowym.|

> [!NOTE]
> Jeśli jest używany w programie systemu Windows, funkcja **_popen** zwraca nieprawidłowy wskaźnik pliku, który powoduje, że program przestaje odpowiadać przez czas nieokreślony. **_popen** działa prawidłowo w aplikacji konsolowej. Aby utworzyć aplikację systemu Windows, która przekierowuje dane wejściowe i wyjściowe, zobacz [Tworzenie procesu podrzędnego z przekierowanymi danymi wejściowymi i wyjściowymi](/windows/win32/ProcThread/creating-a-child-process-with-redirected-input-and-output) w Windows SDK.

**_wpopen** to dwubajtowa wersja **_popen**; argument *ścieżki* **_wpopen** jest ciągiem znaków dwubajtowych. **_wpopen** i **_popen** zachowują się identycznie w inny sposób.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_popen**|\<stdio. h>|
|**_wpopen**|\<stdio. h> lub \<WCHAR. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

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

W tym wyjściu założono, że w bieżącym katalogu znajduje się tylko jeden `.c` plik z rozszerzeniem nazwy pliku.

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

[Proces i kontrola środowiska](../../c-runtime-library/process-and-environment-control.md)\
[_pclose](pclose.md)\
[_pipe](pipe.md)
