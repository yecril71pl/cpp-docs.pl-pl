---
title: getc, getwc
ms.date: 4/2/2020
api_name:
- getwc
- getc
- _o_getc
- _o_getwc
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
- _gettc
- getwc
- _gettchar
- getc
helpviewer_keywords:
- characters, reading
- _gettc function
- getwchar function
- streams, reading characters from
- reading characters from streams
- getc function
- getwc function
- gettc function
ms.assetid: 354ef514-d0c7-404b-92f5-995f6a834bb3
ms.openlocfilehash: 5c05d7a2743cd0c1e843d6895e8f5574031ab098
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344840"
---
# <a name="getc-getwc"></a>getc, getwc

Odczyt znaku ze strumienia.

## <a name="syntax"></a>Składnia

```C
int getc(
   FILE *stream
);
wint_t getwc(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Strumienia*<br/>
Strumień wejściowy.

## <a name="return-value"></a>Wartość zwracana

Zwraca odczyt znaku. Aby wskazać błąd odczytu lub warunek końca pliku, **getc** zwraca **polecenie EOF,** a **getwc** zwraca **polecenie WEOF**. W przypadku **getc**użyj **ferror** lub **feof,** aby sprawdzić, czy nie ma błędu lub końca pliku. Jeśli *strumień* ma **wartość NULL**, **getc** i **getwc** wywołać nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, te funkcje zwracają **EOF** (lub **WEOF** dla **getwc)** i **ustawiają errno** na **EINVAL**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr aby](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) uzyskać więcej informacji na temat tych i innych kodów błędów.

## <a name="remarks"></a>Uwagi

Każda procedura odczytuje pojedynczy znak z pliku w bieżącej pozycji i zwiększa skojarzony wskaźnik pliku (jeśli jest zdefiniowany), aby wskazywał następny znak. Plik jest skojarzony ze *strumieniem*.

Te funkcje blokują wątek wywołujący i dlatego są bezpieczne dla wątków. Aby uzyskać wersję niezablokującą, zobacz [_getc_nolock, _getwc_nolock](getc-nolock-getwc-nolock.md).

Rutynowe uwagi następują.

|Procedura|Uwagi|
|-------------|-------------|
|**getc ( getc )**|Tak samo jak **fgetc**, ale realizowane jako funkcja i jako makro.|
|**getwc ( getwc )**|Szerokoznakowana wersja **getc**. Odczytuje znak wielobajtowy lub szeroki znak w zależności od tego, czy *strumień* jest otwarty w trybie tekstowym, czy w trybie binarnym.|

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettc**|**getc ( getc )**|**getc ( getc )**|**getwc ( getwc )**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**getc ( getc )**|\<stdio.h>|
|**getwc ( getwc )**|\<stdio.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_getc.c
// Use getc to read a line from a file.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;
    FILE* fp;

    // Read a single line from the file "crt_getc.txt".

    fopen_s(&fp, "crt_getc.txt", "r");
    if (!fp)
    {
       printf("Failed to open file crt_getc.txt.\n");
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

### <a name="input-crt_getctxt"></a>Dane wejściowe: crt_getc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
Input was: Line one.
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
