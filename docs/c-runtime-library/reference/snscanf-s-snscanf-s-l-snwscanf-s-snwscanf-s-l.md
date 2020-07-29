---
title: _snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l
ms.date: 11/04/2016
api_name:
- _snwscanf_s_l
- _snwscanf_s
- _snscanf_s
- _snscanf_s_l
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _sntscanf_s
- snscanf_s
- _snwscanf_s_l
- sntscanf_s_l
- snwscanf_s_l
- snwscanf_s
- _snscanf_s
- _snwscanf_s
- snscanf_s_l
- _sntscanf_s_l
- _snscanf_s_l
- sntscanf_s
helpviewer_keywords:
- _snscanf_s_l function
- snwscanf_s function
- _snwscanf_s function
- sntscanf_s_l function
- sntscanf_s function
- _snwscanf_s_l function
- _snscanf_s function
- snscanf_s_l function
- strings [C++], reading data from
- _sntscanf_s_l function
- reading data, strings
- snscanf_s function
- strings [C++], reading
- _sntscanf_s function
- snwscanf_s_l function
ms.assetid: 72356653-7362-461a-af73-597b9c0a8094
ms.openlocfilehash: 6c814d0085fed90f1b3c36684f54368d811c294f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229405"
---
# <a name="_snscanf_s-_snscanf_s_l-_snwscanf_s-_snwscanf_s_l"></a>_snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l

Odczytuje sformatowane dane o określonej długości z ciągu. Są to wersje [_snscanf, _snscanf_l, _snwscanf _snwscanf_l](snscanf-snscanf-l-snwscanf-snwscanf-l.md) z ulepszonymi zabezpieczeniami, jak opisano w [funkcjach zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
int __cdecl _snscanf_s(
   const char * input,
   size_t length,
   const char * format [, argument_list]
);
int __cdecl _snscanf_s_l(
   const char * input,
   size_t length,
   const char * format,
   locale_t locale [, argument_list]
);
int __cdecl _snwscanf_s(
   const wchar_t * input,
   size_t length,
   const wchar_t * format [, argument_list]
);
int __cdecl _snwscanf_s_l(
   const wchar_t * input,
   size_t length,
   const wchar_t * format,
   locale_t locale [, argument_list]
);
```

### <a name="parameters"></a>Parametry

*klawiatur*<br/>
Ciąg wejściowy do sprawdzenia.

*Długość*<br/>
Liczba znaków do sprawdzenia w *danych wejściowych*.

*Formatowanie*<br/>
Jeden lub więcej specyfikatorów formatu.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

*argument_list*<br/>
Opcjonalne argumenty, które mają być przypisane zgodnie z ciągiem formatu.

## <a name="return-value"></a>Wartość zwracana

Obie te funkcje zwracają liczbę pól, które zostały pomyślnie przekonwertowane i przypisane; wartość zwracana nie zawiera pól, które zostały odczytane, ale nie przypisane. Wartość zwracana przez 0 wskazuje, że nie przypisano żadnych pól. Wartość zwracana to **eof** dla błędu lub, jeśli osiągnięto koniec ciągu przed pierwszą konwersją. Aby uzyskać więcej informacji, zobacz [sscanf_s, _sscanf_s_l, swscanf_s _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).

Jeśli *wejście* lub *Format* jest wskaźnikiem o **wartości null** , zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **eof** i ustawiają **errno** na **EINVAL**.

Aby uzyskać informacje o tych i innych kodach błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Ta funkcja jest taka sama jak **sscanf_s** , z tą różnicą, że umożliwia określenie stałej liczby znaków do sprawdzenia z ciągu wejściowego. Aby uzyskać więcej informacji, zobacz [sscanf_s, _sscanf_s_l, swscanf_s _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).

Wymagany jest parametr rozmiaru buforu z znakami pola typu **c**, **c**, **s**, **s**i **[**. Aby uzyskać więcej informacji, zobacz [znaki pola typu scanf](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Parametr size ma typ, a **`unsigned`** nie **size_t**.

Wersje tych funkcji z sufiksem **_l** są identyczne, z tą różnicą, że korzystają z przekazaną parametrem ustawień regionalnych zamiast bieżących ustawień regionalnych wątku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntscanf_s**|**_snscanf_s**|**_snscanf_s**|**_snwscanf_s**|
|**_sntscanf_s_l**|**_snscanf_s_l**|**_snscanf_s_l**|**_snwscanf_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_snscanf_s**, **_snscanf_s_l**|\<stdio.h>|
|**_snwscanf_s**, **_snwscanf_s_l**|\<stdio.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_snscanf_s.c
// This example scans a string of
// numbers, using both the character
// and wide character secure versions
// of the snscanf function.

#include <stdio.h>

int main( )
{
    char        str1[] = "15 12 14...";
    wchar_t     str2[] = L"15 12 14...";
    char        s1[3];
    wchar_t     s2[3];
    int         i;
    float       fp;

    i = _snscanf_s( str1, 6,  "%s %f", s1, 3, &fp);
    printf_s("_snscanf_s converted %d fields: ", i);
    printf_s("%s and %f\n", s1, fp);

    i = _snwscanf_s( str2, 6,  L"%s %f", s2, 3, &fp);
    wprintf_s(L"_snwscanf_s converted %d fields: ", i);
    wprintf_s(L"%s and %f\n", s2, fp);
}
```

```Output
_snscanf_s converted 2 fields: 15 and 12.000000
_snwscanf_s converted 2 fields: 15 and 12.000000
```

## <a name="see-also"></a>Zobacz także

[scanf — Specyfikacja szerokości](../../c-runtime-library/scanf-width-specification.md)<br/>
