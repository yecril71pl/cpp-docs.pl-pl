---
title: _popen, _wpopen
ms.date: 11/04/2016
apiname:
- _popen
- _wpopen
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
ms.openlocfilehash: 5284685f56a73c4c7e48fce981745220651399a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498907"
---
# <a name="popen-wpopen"></a>_popen, _wpopen

Tworzy potok i wykonuje polecenie.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Polecenie*<br/>
Polecenie do wykonania.

*Tryb*<br/>
Tryb zwróconym strumieniu.

## <a name="return-value"></a>Wartość zwracana

Zwraca strumień, który został skojarzony z jednym końcu utworzonego potoku. Drugim końcu potoku jest skojarzony z polecenia zduplikowanych standardowego wejścia lub wyjścia standardowego. Te funkcje zwracają **NULL** w przypadku błędu. Jeśli błąd jest nieprawidłowy parametr, na przykład w przypadku *polecenia* lub *tryb* jest wskaźnikiem wartości null lub *tryb* nie jest prawidłowym trybem **errno** jest równa **EINVAL**. Zobacz sekcję Spostrzeżenia, aby prawidłowe tryby.

Aby uzyskać informacje na temat tych i innych kodów błędu, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Popen —** funkcja tworzy potok i asynchronicznie wykonuje kopię zduplikowanych procesora poleceń przy użyciu określonego ciągu *polecenia*. Ciąg znaków *tryb* określa rodzaj dostępu, w następujący sposób.

|Tryb dostępu|Opis|
|-|-|
|**"r"**|Proces wywołujący może odczytywać standardowe dane wyjściowe polecenia zduplikowanych przy użyciu zwróconym strumieniu.|
|**"w"**|Proces wywołujący może zapisywać standardowe dane wejściowe polecenia zduplikowanych przy użyciu zwróconym strumieniu.|
|**"b"**|Otwórz w trybie binarnym.|
|**"t"**|Otwórz w trybie tekstowym.|

> [!NOTE]
> Jeśli używane w programie Windows **_popen —** funkcja zwraca wskaźnik nieprawidłowy plik, który powoduje, że program przestanie odpowiadać na czas nieokreślony. **_popen —** działa poprawnie, w aplikacji konsoli. Aby utworzyć aplikację Windows, który przekierowuje dane wejściowe i wyjściowe, zobacz [tworzenia procesu podrzędnego z przekierowanie danych wejściowych i wyjściowych](/windows/desktop/ProcThread/creating-a-child-process-with-redirected-input-and-output) w zestawie Windows SDK.

**_wpopen —** to wersja znaku dwubajtowego **_popen —**; *ścieżki* argument **_wpopen —** jest ciągiem znaku dwubajtowego. **_wpopen —** i **_popen —** zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen —**|**_popen —**|**_popen —**|**_wpopen —**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_popen —**|\<stdio.h>|
|**_wpopen —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

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
      printf(psBuffer);
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

### <a name="sample-output"></a>Przykładowe dane wyjściowe

Te dane wyjściowe przyjęto założenie, że istnieje tylko jeden plik w bieżącym katalogu z rozszerzeniem nazwy pliku .c.

```Output
Volume in drive C is CDRIVE
Volume Serial Number is 0E17-1702

Directory of D:\proj\console\test1

07/17/98  07:26p                   780 popen.c
               1 File(s)            780 bytes
                             86,597,632 bytes free

Process returned 0
```

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pclose](pclose.md)<br/>
[_pipe](pipe.md)<br/>
