---
title: vfscanf, vfwscanf
ms.date: 11/04/2016
api_name:
- vfwscanf
- vfscanf
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
- vfwscanf
- _vftscanf
- vfscanf
ms.assetid: c06450ef-03f1-4d24-a8ac-d2dd98847918
ms.openlocfilehash: 72591c9fa91855745f45f3f77c88dd0ed5b001a0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945521"
---
# <a name="vfscanf-vfwscanf"></a>vfscanf, vfwscanf

Odczytuje sformatowane dane ze strumienia. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [vfscanf_s, vfwscanf_s](vfscanf-s-vfwscanf-s.md).

## <a name="syntax"></a>Składnia

```C
int vfscanf(
   FILE *stream,
   const char *format,
   va_list argptr
);
int vfwscanf(
   FILE *stream,
   const wchar_t *format,
   va_list argptr
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

Każda z tych funkcji zwraca liczbę pól, które zostały pomyślnie przekonwertowane i przypisane; wartość zwracana nie zawiera pól, które są odczytywane, ale nie są przypisane. Wartość zwracana przez 0 wskazuje, że nie przypisano żadnych pól. Jeśli wystąpi błąd lub osiągnięto koniec strumienia pliku przed pierwszą konwersją, wartość zwracana to **eof** dla **vfscanf** i **vfwscanf**.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *strumień* lub *Format* jest pustym wskaźnikiem, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **eof** i ustawiają **errno** na **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **vfscanf** odczytuje dane z bieżącego położenia *strumienia* do lokalizacji, które są określone przez listę argumentów *arglist* . Każdy argument na liście musi być wskaźnikiem do zmiennej typu odpowiadającego specyfikatorowi typu w *formacie*. *Format* kontroluje interpretację pól wejściowych i ma taką samą formę i funkcję jak argument *formatu* dla **scanf**; Opis *formatu*można znaleźć w temacie [scanf](scanf-scanf-l-wscanf-wscanf-l.md) .

**vfwscanf** to dwubajtowa wersja **vfscanf**; argument formatu **vfwscanf** jest ciągiem znaków dwubajtowych. Te funkcje zachowują się identycznie, jeśli strumień jest otwarty w trybie ANSI. **vfscanf** nie obsługuje danych wejściowych ze strumienia Unicode.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftscanf**|**vfscanf**|**vfscanf**|**vfwscanf**|

Aby uzyskać więcej informacji, zobacz [Formatowanie pól specyfikacji: scanf i wscanf Functions](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**vfscanf**|\<stdio.h>|
|**vfwscanf**|\<stdio. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_vfscanf.c
// compile with: /W3
// This program writes formatted
// data to a file. It then uses vfscanf to
// read the various data back from the file.

#include <stdio.h>
#include <stdarg.h>

FILE *stream;

int call_vfscanf(FILE * istream, char * format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vfscanf(istream, format, arglist);
    va_end(arglist);
    return result;
}

int main(void)
{
    long l;
    float fp;
    char s[81];
    char c;

    if (fopen_s(&stream, "vfscanf.out", "w+") != 0)
    {
        printf("The file vfscanf.out was not opened\n");
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
        call_vfscanf(stream, "%s %ld %f%c", s, &l, &fp, &c);

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
[_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
[vfscanf_s, vfwscanf_s](vfscanf-s-vfwscanf-s.md)<br/>
