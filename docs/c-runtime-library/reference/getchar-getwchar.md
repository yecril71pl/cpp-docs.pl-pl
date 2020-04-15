---
title: getchar, getwchar
ms.date: 4/2/2020
api_name:
- getchar
- getwchar
- _o_getchar
- _o_getwchar
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
- getwchar
- GetChar
helpviewer_keywords:
- gettchar function
- characters, reading
- getwchar function
- _gettchar function
- standard input, reading from
ms.assetid: 19fda588-3e33-415c-bb60-dd73c028086a
ms.openlocfilehash: 4311b5b896a5a406ebe14f09e7bb525cb47951b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344611"
---
# <a name="getchar-getwchar"></a>getchar, getwchar

Odczytuje znak ze standardowego wejścia.

## <a name="syntax"></a>Składnia

```C
int getchar();
wint_t getwchar();
```

## <a name="return-value"></a>Wartość zwracana

Zwraca odczyt znaku. Aby wskazać błąd odczytu lub warunek końca pliku, **getchar** zwraca **EOF,** a **getwchar** zwraca **POLECENIE WEOF**. W przypadku **getcharu**użyj **ferror** lub **feof,** aby sprawdzić, czy nie ma błędu lub końca pliku.

## <a name="remarks"></a>Uwagi

Każda procedura odczytuje pojedynczy znak ze **stdin** i zwiększa skojarzony wskaźnik pliku, aby wskazać następny znak. **getchar** jest taki sam jak [_fgetchar](fgetc-fgetwc.md), ale jest realizowany jako funkcja i jako makro.

Te funkcje blokują wątek wywołujący i dlatego są bezpieczne dla wątków. Aby uzyskać wersję niezablokującą, zobacz [_getchar_nolock _getwchar_nolock](getchar-nolock-getwchar-nolock.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettchar**|**Getchar**|**Getchar**|**getwchar ( getwchar )**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Getchar**|\<stdio.h>|
|**getwchar ( getwchar )**|\<stdio.h> lub \<wchar.h>|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej systemu Windows (UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą, **stdin**, **stdout**i **stderr**, muszą zostać przekierowane, zanim funkcje c w czasie wykonywania mogą z nich korzystać w aplikacjach platformy uniwersalnej systemu Windows. Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_getchar.c
// Use getchar to read a line from stdin.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;

    for (i = 0; (i < 80) && ((ch = getchar()) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character
    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);
}
```

```Output

This textInput was: This text
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
