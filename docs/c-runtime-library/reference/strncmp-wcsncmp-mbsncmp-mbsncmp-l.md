---
title: strncmp, wcsncmp, _mbsncmp, _mbsncmp_l
ms.date: 4/2/2020
api_name:
- strncmp
- _mbsncmp
- wcsncmp
- _mbsncmp_l
- _o__mbsncmp
- _o__mbsncmp_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ftcsnccmp
- _ftcsncmp
- _tcsncmp
- _tcsnccmp
- strncmp
- _mbsncmp
- wcsncmp
helpviewer_keywords:
- _tcsnccmp function
- ftcsncmp function
- wcsncmp function
- _ftcsncmp function
- _mbsncmp function
- tcsncmp function
- mbsncmp function
- _mbsncmp_l function
- mbsncmp_l function
- strncmp function
- strings [C++], comparing characters of
- string comparison [C++], strncmp function
- _tcsncmp function
- tcsnccmp function
- ftcsnccmp function
- characters [C++], comparing
- _ftcsnccmp function
ms.assetid: 2fdbf4e6-77da-4b59-9086-488f6066b8af
ms.openlocfilehash: fa253bbf7b0ea2ae9993edb12843245b2a1065ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364188"
---
# <a name="strncmp-wcsncmp-_mbsncmp-_mbsncmp_l"></a>strncmp, wcsncmp, _mbsncmp, _mbsncmp_l

Porównuje do określonej liczby znaków dwóch ciągów.

> [!IMPORTANT]
> **_mbsncmp** i **_mbsncmp_l** nie mogą być używane w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int strncmp(
   const char *string1,
   const char *string2,
   size_t count
);
int wcsncmp(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsncmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsncmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);int _mbsnbcmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*ciąg1*, *ciąg2*<br/>
Ciągi do porównania.

*Liczba*<br/>
Liczba znaków do porównania.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwracana wartość wskazuje relację podciągów *string1* i *string2* w następujący sposób.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*podciąg ciąg1* mniejszy niż podciąg *string2*|
|0|*podciąg ciąg1* identyczny z podciągiem *string2*|
|> 0|*podciąg ciąg1* większy niż podciąg *string2*|

W sprawie błędu sprawdzania poprawności parametrów **_mbsncmp** i **_mbsncmp_l** zwracają **_NLSCMPERROR** \<, który jest zdefiniowany \<w> string.h i mbstring.h>.

## <a name="remarks"></a>Uwagi

Funkcja **strncmp** wykonuje porównanie porządkowe co najwyżej pierwszych znaków *zliczania* w *ciągu1* i *string2* i zwraca wartość wskazującą relację między podciągami. **strncmp** jest wersją **_strnicmp**uwzględniającą wielkość liter . **wcsncmp** i **_mbsncmp** są wersjami **_wcsnicmp** i **_mbsnicmp**z uwzględnieniem wielkości liter.

**wcsncmp** i **_mbsncmp** są wersjami **strncmp o**szerokich i wielobajtowych znakach. Argumenty **wcsncmp** są ciągi znaków o szerokich znakach; **_mbsncmp** są ciągami znaków wielobajtowych. **_mbsncmp** rozpoznaje sekwencje znaków wielobajtowych zgodnie ze stroną kodową wielobajtową i zwraca **_NLSCMPERROR** na błąd.

Ponadto **_mbsncmp** i **_mbsncmp_l** sprawdzania poprawności parametrów. Jeśli *string1* lub *string2* jest wskaźnikiem null, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w programie [Sprawdzanie poprawności parametru.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **_mbsncmp** i **_mbsncmp_l** zwrócić **_NLSCMPERROR** i ustawić **errno** na **EINVAL**. **strncmp** i **wcsncmp** nie weryfikują swoich parametrów. Te funkcje zachowują się identycznie w przeciwnym razie.

Na zachowanie porównania **_mbsncmp** i **_mbsncmp_l** ma wpływ ustawienie ustawienia **kategorii LC_CTYPE** ustawień ustawień regionalnych. Służy to do wykrywania bajtów wiodących i końcowych znaków wielobajtowych. Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). Funkcja **_mbsncmp** używa bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. Funkcja **_mbsncmp_l** jest identyczna, z tą różnicą, że zamiast tego używa parametru *ustawień regionalnych.* Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md). Jeśli ustawienia regionalne są ustawieniami lokalnymi jedno bajtowymi, zachowanie tych funkcji jest identyczne z **strncmp**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccmp**|**strncmp (strncmp)**|**_mbsncmp**|**wcsncmp**|
|**_tcsncmp**|**strncmp (strncmp)**|**_mbsnbcmp**|**wcsncmp**|
|**_tccmp**|Mapowanie do funkcji makra lub wbudowanej|**_mbsncmp**|Mapowanie do funkcji makra lub wbudowanej|
|**nie dotyczy**|**nie dotyczy**|**_mbsncmp_l**|**nie dotyczy**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strncmp (strncmp)**|\<string.h>|
|**wcsncmp**|\<string.h> lub \<wchar.h>|
|**_mbsncmp** **, _mbsncmp_l**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strncmp.c
#include <string.h>
#include <stdio.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown fox jumps over the lazy dog";

int main( void )
{
   char tmp[20];
   int result;
   printf( "Compare strings:\n      %s\n      %s\n\n",
           string1, string2 );
   printf( "Function:   strncmp (first 10 characters only)\n" );
   result = strncmp( string1, string2 , 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n\n", tmp );
   printf( "Function:   strnicmp _strnicmp (first 10 characters only)\n" );
   result = _strnicmp( string1, string2, 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
      The quick brown dog jumps over the lazy fox
      The QUICK brown fox jumps over the lazy dog

Function:   strncmp (first 10 characters only)
Result:      String 1 is greater than string 2

Function:   strnicmp _strnicmp (first 10 characters only)
Result:      String 1 is equal to string 2
```

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll — Funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
