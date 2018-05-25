---
title: _strnset —, _strnset_l —, _wcsnset —, _wcsnset_l —, _mbsnset —, _mbsnset_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsnset
- _strnset
- _mbsnset_l
- _wcsnset_l
- _wcsnset
- _strnset_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcsncset_l
- mbsnset_l
- _tcsnset_l
- _fstrnset
- _wcsnset_l
- _ftcsnset
- wcsnset_l
- _mbsnset_l
- _strnset
- _tcsnset
- _strnset_l
- mbsnset
- strnset_l
- _mbsnset
- _wcsnset
- _tcsncset
dev_langs:
- C++
helpviewer_keywords:
- _wcsnset function
- strnset_l function
- tcsnset function
- tcsncset function
- characters [C++], initializing to formats
- mbsnset function
- _tcsnset_l function
- _mbsnset function
- _strnset function
- _tcsncset_l function
- mbsnset_l function
- _tcsnset function
- initializing characters
- _tcsncset function
- ftcsnset function
- wcsnset_l function
- _ftcsnset function
- _wcsnset_l function
- _fstrnset function
- _mbsnset_l function
- _strnset_l function
- fstrnset function
- strings [C++], initializing
- tcsnset_l function
ms.assetid: 3f306489-5763-48e5-b939-aefee7c94ef5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9348b2797b137599e8c7f54e41e493003bc4fc58
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="strnset-strnsetl-wcsnset-wcsnsetl-mbsnset-mbsnsetl"></a>_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l

Inicjuje znaków ciągu do danego znaku. Istnieją bardziej bezpieczne wersje tych funkcji; zobacz [_strnset_s —, _strnset_s_l —, _wcsnset_s —, _wcsnset_s_l, _mbsnset_s —, _mbsnset_s_l —](strnset-s-strnset-s-l-wcsnset-s-wcsnset-s-l-mbsnset-s-mbsnset-s-l.md).

> [!IMPORTANT]
> **_mbsnset —** i **_mbsnset_l —** nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
char *_strnset(
   char *str,
   int c,
   size_t count
);
char *_strnset_l(
   char *str,
   int c,
   size_t count,
   locale_t locale
);
wchar_t *_wcsnset(
   wchar_t *str,
   wchar_t c,
   size_t count
);
wchar_t *_wcsnset_l(
   wchar_t *str,
   wchar_t c,
   size_t count,
   _locale_t locale
);
unsigned char *_mbsnset(
   unsigned char *str,
   unsigned int c,
   size_t count
);
unsigned char *_mbsnset_l(
   unsigned char *str,
   unsigned int c,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Ciąg, który ma zostać zmienione.

*c*<br/>
Ustawienie znaków.

*Liczba*<br/>
Liczba znaków, które można ustawić.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do ciągu zmieniony.

## <a name="remarks"></a>Uwagi

**_Strnset —** funkcja ustawia co najwyżej pierwszy *liczba* znaków *str* do *c* (przekonwertować **char**). Jeśli *liczba* jest większa niż długość *str*, długość *str* jest używany zamiast *liczba*.

**_wcsnset —** i **_mbsnset —** znaków dwubajtowych i znaków wielobajtowych wersji **_strnset —**. Argumenty typu string i zwracana wartość **_wcsnset —** są znaków dwubajtowych ciągi; tych **_mbsnset —** są ciągami znaków wielobajtowych. Te trzy funkcje działają tak samo w przeciwnym razie wartość.

**_mbsnset —** weryfikuje jego parametrów; Jeśli *str* wskaźnika o wartości null, jest program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli jest dozwolone wykonywanie, aby kontynuować, **_mbsnset —** zwraca **NULL** i ustawia **errno** do **einval —**. **_strnset —** i **_wcsnset —** nie weryfikują ich parametrów.

Wartość wyjściowa jest zagrożony ustawienie **lc_ctype —** ustawienie kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez **_l** Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych Przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnset —**|**_strnset**|**_mbsnbset —**|**_wcsnset**|
|**_tcsnset_l —**|**_strnset_l**|**_mbsnbset_l**|**_wcsnset_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strnset**|\<string.h>|
|**_strnset_l**|\<tchar.h >|
|**_wcsnset**|\<String.h > lub \<wchar.h >|
|**_wcsnset_l**|\<tchar.h >|
|**_mbsnset —**, **_mbsnset_l —**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strnset.c
// compile with: /W3
#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 characters of string to be *'s */
   printf( "Before: %s\n", string );
   _strnset( string, '*', 4 ); // C4996
   // Note: _strnset is deprecated; consider using _strnset_s
   printf( "After:  %s\n", string );
}
```

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
