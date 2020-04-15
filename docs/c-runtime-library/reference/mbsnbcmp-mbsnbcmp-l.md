---
title: _mbsnbcmp, _mbsnbcmp_l
ms.date: 4/2/2020
api_name:
- _mbsnbcmp
- _mbsnbcmp_l
- _o__mbsnbcmp
- _o__mbsnbcmp_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsnbcmp
- tcsnbmp
- _mbsnbcmp_l
- mbsnbcmp_l
- _mbsnbcmp
helpviewer_keywords:
- mbsnbcmp_l function
- mbsnbcmp function
- tcsncmp function
- _mbsnbcmp_l function
- _tcsncmp function
- _mbsnbcmp function
ms.assetid: dbc99e50-cf85-4e57-a13f-067591f18ac8
ms.openlocfilehash: 2334d7755a3eaf3fb973783db17ca398e6b7f0b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340694"
---
# <a name="_mbsnbcmp-_mbsnbcmp_l"></a>_mbsnbcmp, _mbsnbcmp_l

Porównuje pierwsze **n** bajtów dwóch ciągów znaków wielobajtowych.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _mbsnbcmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbcmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*ciąg1*, *ciąg2*<br/>
Ciągi do porównania.

*Liczba*<br/>
Liczba bajtów do porównania.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwracana wartość wskazuje relację porządkową między podciągami *string1* i *string2*.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*podciąg string1* jest mniejszy niż podciąg *string2.*|
|0|*podciąg string1* jest identyczny z podciągiem *string2.*|
|> 0|*podciąg 1* jest większy niż podciąg *string2.*|

W sprawie błędu sprawdzania poprawności parametrów **_mbsnbcmp** i **_mbsnbcmp_l** zwracają **_NLSCMPERROR**, \<która jest zdefiniowana w \<> string.h i mbstring.h>.

## <a name="remarks"></a>Uwagi

Funkcje **_mbsnbcmp** porównać co najwyżej pierwsze *bajty liczby* w *string1* i *string2* i zwracać wartość, która wskazuje relację między podciągami. **_mbsnbcmp** jest wersją **_mbsnbicmp**uwzględniającą wielkość liter . W przeciwieństwie do **_mbsnbcoll** **, _mbsnbcmp** nie ma wpływu kolejność sortowania ustawień regionalnych. **_mbsnbcmp** rozpoznaje sekwencje znaków wielobajtowych zgodnie z bieżącą [wielobajtową stroną kodową](../../c-runtime-library/code-pages.md).

**_mbsnbcmp** przypomina **_mbsncmp**, z tą różnicą, że **_mbsncmp** porównuje ciągi według znaków, a nie bajtów.

Na wartość danych wyjściowych ma wpływ ustawienie **kategorii LC_CTYPE** ustawień regionalnych, które określa bajty potencjalnego klienta i bajty końcowe znaków wielobajtowych. Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). Funkcja **_mbsnbcmp** używa bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. Funkcja **_mbsnbcmp_l** jest identyczna, z tą różnicą, że zamiast tego używa parametru *ustawień regionalnych.* Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli *ciąg1* lub *ciąg2* jest wskaźnikiem null, te funkcje wywołują nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcje zwracają **_NLSCMPERROR** i **errno** jest ustawiona na **EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i nie _MBCS zdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|---------------------------------------|--------------------|-----------------------|
|**_tcsncmp**|[strncmp (strncmp)](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|**_mbsnbcmp**|[wcsncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|
|**_tcsncmp_l**|[strncmp (strncmp)](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|**_mbsnbcml**|[wcsncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbcmp**|\<mbstring.h>|
|**_mbsnbcmp_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_mbsnbcmp.c
#include <mbstring.h>
#include <stdio.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown fox jumps over the lazy dog";

int main( void )
{
   char tmp[20];
   int result;
   printf( "Compare strings:\n          %s\n", string1 );
   printf( "          %s\n\n", string2 );
   printf( "Function: _mbsnbcmp (first 10 characters only)\n" );
   result = _mbsncmp( string1, string2 , 10 );
   if( result > 0 )
      _mbscpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      _mbscpy_s( tmp, sizeof(tmp), "less than" );
   else
      _mbscpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:   String 1 is %s string 2\n\n", tmp );
   printf( "Function: _mbsnicmp _mbsnicmp (first 10 characters only)\n" );
   result = _mbsnicmp( string1, string2, 10 );
   if( result > 0 )
      _mbscpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      _mbscpy_s( tmp, sizeof(tmp), "less than" );
   else
      _mbscpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:   String 1 is %s string 2\n\n", tmp );
}
```

### <a name="output"></a>Dane wyjściowe

```Output
Compare strings:
          The quick brown dog jumps over the lazy fox
          The QUICK brown fox jumps over the lazy dog

Function: _mbsnbcmp (first 10 characters only)
Result:   String 1 is greater than string 2

Function: _mbsnicmp _mbsnicmp (first 10 characters only)
Result:   String 1 is equal to string 2
```

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
