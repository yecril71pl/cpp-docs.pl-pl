---
title: getc, getwc
ms.date: 11/04/2016
apiname:
- getwc
- getc
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
ms.openlocfilehash: bbaee79eac6802959a11f7f1ba30eaf590ecf2f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664870"
---
# <a name="getc-getwc"></a>getc, getwc

Przeczytaj znak ze strumienia.

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

*Stream*<br/>
Strumień wejściowy.

## <a name="return-value"></a>Wartość zwracana

Zwraca znak odczytywany. Aby wskazać błąd odczytu lub warunek końca pliku **getc —** zwraca **EOF**, i **getwc —** zwraca **WEOF**. Aby uzyskać **getc —**, użyj **ferror** lub **feof** pod kątem wystąpienia błędu lub końca pliku. Jeśli *strumienia* jest **NULL**, **getc —** i **getwc —** wywołują nieprawidłowy parametr uchwytu, zgodnie z opisem w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **EOF** (lub **WEOF** dla **getwc —**) i ustaw **errno** do  **EINVAL**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędu,.

## <a name="remarks"></a>Uwagi

Każda procedura odczytuje pojedynczy znak z pliku w bieżącym położeniu i zwiększa skojarzony wskaźnik pliku (Jeżeli zdefiniowane) aby wskazywała na następny znak. Plik jest skojarzony z *strumienia*.

Te funkcje blokują wywołania wątku i dlatego jest metodą o bezpiecznych wątkach. Dla wersji bez blokady, zobacz [_getc_nolock —, _getwc_nolock —](getc-nolock-getwc-nolock.md).

Wykonaj rutynowe specyficzne uwagi.

|Procedura|Uwagi|
|-------------|-------------|
|**getc**|Taki sam jak **fgetc —**, ale zaimplementowane jako funkcja i makra.|
|**getwc**|Wersja znaków dwubajtowych **getc —**. Odczytuje znak wielobajtowy lub znak dwubajtowy ze czy *strumienia* jest otwarty w trybie tekstu lub w trybie binarnym.|

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettc —**|**getc**|**getc**|**getwc**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**getc**|\<stdio.h>|
|**getwc**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

### <a name="input-crtgetctxt"></a>Dane wejściowe: crt_getc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
Input was: Line one.
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
