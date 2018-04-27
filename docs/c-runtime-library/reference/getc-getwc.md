---
title: getc —, getwc — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20845c8e1dbe24b30032cfb1fbffb5d24c6cfdc8
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="getc-getwc"></a>getc, getwc

Znak odczytu ze strumienia.

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

*Strumień*<br/>
Strumień wejściowy.

## <a name="return-value"></a>Wartość zwracana

Zwraca znak do odczytu. Błąd odczytu lub warunek plik końcowy **getc —** zwraca **EOF**, i **getwc —** zwraca **weof —**. Dla **getc —**, użyj **ferror —** lub **feof —** do sprawdzania błędów lub na końcu pliku. Jeśli *strumienia* jest **NULL**, **getc —** i **getwc —** Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają **EOF** (lub **weof —** dla **getwc —**) i ustawić **errno** do  **Einval —**.

Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędów.

## <a name="remarks"></a>Uwagi

Każdej procedury odczytuje pojedynczy znak z pliku w bieżącej pozycji i zwiększa wskaźnik skojarzony plik (jeśli jest zdefiniowana) aby wskazywały na następny znak. Plik jest skojarzony z *strumienia*.

Te funkcje Zablokuj wątek wywołujący i w związku z tym są wątkowo. Wersja — blokowanie dla [_getc_nolock —, _getwc_nolock —](getc-nolock-getwc-nolock.md).

Uwagi dotyczące procedury należy wykonać.

|Procedura|Uwagi|
|-------------|-------------|
|**getc**|Taki sam jak **fgetc —**, ale zaimplementowane jako funkcję, a makra.|
|**getwc**|Wersja znaków dwubajtowych **getc —**. Odczytuje znaków wielobajtowych lub znaków dwubajtowych zgodnie z czy *strumienia* jest otwarty w trybie tekst lub binarny.|

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
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

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
