---
title: _popen —, _wpopen — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- tpopen function
- pipes, creating
- _popen function
- _tpopen function
- popen function
- wpopen function
- _wpopen function
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 39ed5841c50dea2aad79db3ee73589fcaa5aa39b
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="popen-wpopen"></a>_popen, _wpopen

Tworzy potoku i wykonuje polecenie.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*polecenie*<br/>
Polecenie do wykonania.

*Tryb*<br/>
Tryb zwrócony strumień.

## <a name="return-value"></a>Wartość zwracana

Zwraca strumień skojarzona jeden element end utworzony potoku. Po drugiej stronie potoku jest skojarzony z polecenia uruchomionego standardowego wejścia lub wyjścia standardowego. Funkcje zwracają **NULL** w przypadku wystąpienia błędu. Jeśli błąd jest nieprawidłowy parametr, np. Jeśli *polecenia* lub *tryb* jest wskaźnika o wartości null, lub *tryb* nie jest prawidłowym trybem **errno** ma ustawioną wartość **Einval —**. W sekcji uwag prawidłowe tryby.

Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Popen —** funkcja tworzy potoku i asynchronicznie wykonuje kopię zduplikowanego procesora poleceń z określonego ciągu *polecenia*. Ciąg znaków *tryb* Określa typ dostępu, w następujący sposób.

**"r"** proces wywołujący może odczytywać wyjścia standardowego polecenia uruchomionego za pomocą strumienia zwrócone.

**"w"** proces wywołujący może zapisać standardowe dane wejściowe polecenia uruchomionego za pomocą strumienia zwrócone.

**"b"** otwarty w trybie binarnym.

**"t"** otwarte w trybie tekstowym.

> [!NOTE]
> Jeśli używane w programie Windows **_popen —** funkcja zwraca wskaźnik nieprawidłowy plik, który powoduje, że program przestanie odpowiadać nieskończoność. **_popen —** działa prawidłowo w aplikacji konsoli. Do tworzenia aplikacji systemu Windows, który przekierowuje dane wejściowe i wyjściowe, zobacz [tworzenie procesu podrzędnego z Przekierowanie wejściowe i wyjściowe](http://msdn.microsoft.com/library/windows/desktop/ms682499) w zestawie Windows SDK.

**_wpopen —** jest wersja znaków dwubajtowych **_popen —**; *ścieżki* argument **_wpopen —** jest ciągiem znaków dwubajtowych. **_wpopen —** i **_popen —** zachowują się tak samo w przeciwnym razie wartość.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen —**|**_popen —**|**_popen —**|**_wpopen —**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_popen —**|\<stdio.h>|
|**_wpopen —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

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
