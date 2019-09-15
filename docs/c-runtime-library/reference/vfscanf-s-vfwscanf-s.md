---
title: vfscanf_s, vfwscanf_s
ms.date: 11/04/2016
api_name:
- vfscanf_s
- vfwscanf_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- vfscanf_s
- vfwscanf_s
- _vftscanf_s
ms.assetid: 9b0133f0-9a18-4581-b24b-3b72683ad432
ms.openlocfilehash: 2c6f3504c9c12ad5429a1b9649eda351c473671a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957377"
---
# <a name="vfscanf_s-vfwscanf_s"></a>vfscanf_s, vfwscanf_s

Odczytuje sformatowane dane ze strumienia. Te wersje programu vfscanf vfwscanf mają ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
int vfscanf_s(
   FILE *stream,
   const char *format,
   va_list arglist
);
int vfwscanf_s(
   FILE *stream,
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Wskaźnik do struktury **pliku** .

*format*<br/>
Ciąg kontroli formatu.

*arglist*<br/>
Lista argumentów zmiennych.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca liczbę pól, które zostały pomyślnie przekonwertowane i przypisane; wartość zwracana nie zawiera pól, które zostały odczytane, ale nie przypisane. Wartość zwracana przez 0 wskazuje, że nie przypisano żadnych pól. Jeśli wystąpi błąd lub osiągnięto koniec strumienia pliku przed pierwszą konwersją, wartość zwracana to **eof** dla **vfscanf_s** i **vfwscanf_s**.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *strumień* jest nieprawidłowym wskaźnikiem pliku lub *Format* jest wskaźnikiem typu null, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **eof** i ustawiają **errno** na **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **vfscanf_s** odczytuje dane z bieżącego położenia *strumienia* do lokalizacji, które są określone przez listę argumentów *arglist* (jeśli istnieje). Każdy argument na liście musi być wskaźnikiem do zmiennej typu odpowiadającego specyfikatorowi typu w *formacie*. *Format* kontroluje interpretację pól wejściowych i ma taką samą formę i funkcję jak argument *formatu* dla **scanf_s**; Zobacz sekcję [Specyfikacja formatu: scanf i wscanf funkcje](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md) opisujące *Format*. **vfwscanf_s** to dwubajtowa wersja **vfscanf_s**; argument formatu **vfwscanf_s** jest ciągiem znaków dwubajtowych. Te funkcje zachowują się identycznie, jeśli strumień jest otwarty w trybie ANSI. **vfscanf_s** obecnie nie obsługuje danych wejściowych ze strumienia Unicode.

Główna różnica między bardziej bezpiecznymi funkcjami (które mają sufiks **_s** ) i innymi wersjami polega na tym, że bezpieczniejsze funkcje wymagają rozmiaru w znakach każdego języka **c**, **c**, **s**, **s**i **[** Type, aby przekazanie jako argument bezpośrednio po zmiennej. Aby uzyskać więcej informacji, zobacz [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) i [scanf Width Specification](../../c-runtime-library/scanf-width-specification.md).

> [!NOTE]
> Parametr size jest typu **unsigned**, not **size_t**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftscanf_s**|**vfscanf_s**|**vfscanf_s**|**vfwscanf_s**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**vfscanf_s**|\<stdio.h>|
|**vfwscanf_s**|\<stdio. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_vfscanf_s.c
// compile with: /W3
// This program writes formatted
// data to a file. It then uses vfscanf_s to
// read the various data back from the file.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

FILE *stream;

int call_vfscanf_s(FILE * istream, char * format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vfscanf_s(istream, format, arglist);
    va_end(arglist);
    return result;
}

int main(void)
{
    long l;
    float fp;
    char s[81];
    char c;

    if (fopen_s(&stream, "vfscanf_s.out", "w+") != 0)
    {
        printf("The file vfscanf_s.out was not opened\n");
    }
    else
    {
        fprintf(stream, "%s %ld %f%c", "a-string",
            65000, 3.14159, 'x');
        // Security caution!
        // Beware loading data from a file without confirming its size,
        // as it may lead to a buffer overrun situation.

        // Set pointer to beginning of file:
        fseek(stream, 0L, SEEK_SET);

        // Read data back from file:
        call_vfscanf_s(stream, "%s %ld %f%c", s, _countof(s), &l, &fp, &c, 1);

        // Output data read:
        printf("%s\n", s);
        printf("%ld\n", l);
        printf("%f\n", fp);
        printf("%c\n", c);

        fclose(stream);
    }
}
```

```Output
a-string
65000
3.141590
x
```

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)<br/>
[fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[vfscanf, vfwscanf](vfscanf-vfwscanf.md)<br/>
