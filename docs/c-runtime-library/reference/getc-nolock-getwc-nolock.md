---
title: _getc_nolock, _getwc_nolock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _getc_nolock
- _getwc_nolock
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
- getc_nolock
- _gettc_nolock
- _getc_nolock
- getwc_nolock
- gettc_nolock
- _getwc_nolock
dev_langs:
- C++
helpviewer_keywords:
- characters, reading
- _getc_nolock function
- _getwc_nolock function
- getwc_nolock function
- streams, reading characters from
- reading characters from streams
- getc_nolock function
- gettc_nolock function
- _gettc_nolock function
ms.assetid: eb37b272-e177-41c9-b077-12ce7ffd3b88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c727f43748be8beb327115350923ee3ea9994db
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="getcnolock-getwcnolock"></a>_getc_nolock, _getwc_nolock

Odczytuje znak ze strumienia.

## <a name="syntax"></a>Składnia

```C
int _getc_nolock(
   FILE *stream
);
wint_t _getwc_nolock(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Strumień*<br/>
Strumień wejściowy.

## <a name="return-value"></a>Wartość zwracana

Zobacz [getc —, getwc —](getc-getwc.md).

## <a name="remarks"></a>Uwagi

Te funkcje są takie same jak **getc —** i **getwc —** z tą różnicą, że nie należy blokować wątek wywołujący. Może być szybsze, ponieważ nie wiążą się z obciążenie zablokowania inne wątki. Ich używać tylko w kontekstach wątkowo, np. aplikacje jednowątkowe lub gdzie wywoływania zakres już obsługuje izolacji wątku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_gettc_nolock —**|**getc_nolock —**|**getc_nolock —**|**getwc_nolock —**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**getc_nolock —**|\<stdio.h>|
|**getwc_nolock —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_getc_nolock.c
// Use getc to read a line from a file.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;
    FILE* fp;

    // Read a single line from the file "crt_getc_nolock.txt".
    fopen_s(&fp, "crt_getc_nolock.txt", "r");
    if (!fp)
    {
       printf("Failed to open file crt_getc_nolock.txt.\n");
       exit(1);
    }

    for (i = 0; (i < 80) && ((ch = getc(fp)) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character
    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);

    fclose(fp);
}
```

### <a name="input-crtgetcnolocktxt"></a>Dane wejściowe: crt_getc_nolock.txt

```Input
Line the first.
Line the second.
```

### <a name="output"></a>Dane wyjściowe

```Output
Input was: Line the first.
```

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
