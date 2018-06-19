---
title: _mbsnbcmp —, _mbsnbcmp_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsnbcmp
- _mbsnbcmp_l
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
apitype: DLLExport
f1_keywords:
- mbsnbcmp
- tcsnbmp
- _mbsnbcmp_l
- mbsnbcmp_l
- _mbsnbcmp
dev_langs:
- C++
helpviewer_keywords:
- mbsnbcmp_l function
- mbsnbcmp function
- tcsncmp function
- _mbsnbcmp_l function
- _tcsncmp function
- _mbsnbcmp function
ms.assetid: dbc99e50-cf85-4e57-a13f-067591f18ac8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a21d19a3de6a047366497283f2e8515aca37794
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404639"
---
# <a name="mbsnbcmp-mbsnbcmpl"></a>_mbsnbcmp, _mbsnbcmp_l

Porównuje pierwszy **n** bajtów dwa ciągi znaków wielobajtowych.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Wartości zwracanej wskazuje numer porządkowy relację między podciągów *ciąg1* i *ciąg2*.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*ciąg1* podciąg jest mniejsza niż *ciąg2* podciąg.|
|0|*ciąg1* podciąg jest taki sam jak *ciąg2* podciąg.|
|> 0|*ciąg1* podciąg jest większa niż *ciąg2* podciąg.|

Parametr błędu sprawdzania poprawności **_mbsnbcmp —** i **_mbsnbcmp_l —** zwracać **_NLSCMPERROR**, która jest zdefiniowana w \<string.h > i \< mbstring.h >.

## <a name="remarks"></a>Uwagi

**_Mbsnbcmp —** funkcje co najwyżej porównania pierwszy *liczba* bajtów w *ciąg1* i *ciąg2* i zwraca wartość wskazującą, Relacja między podciągów. **_mbsnbcmp —** jest rozróżniana wielkość liter wersja **_mbsnbicmp —**. W odróżnieniu od **_mbsnbcoll —**, **_mbsnbcmp —** nie ma wpływu na kolejność sortowania ustawień regionalnych. **_mbsnbcmp —** rozpoznaje wielobajtowych sekwencji znaków zgodnie z bieżącym wielobajtowe [strona kodowa](../../c-runtime-library/code-pages.md).

**_mbsnbcmp —** podobny **_mbsncmp —**, ale **_mbsncmp —** porównuje ciągi znaków, a nie w bajtach.

Wartość wyjściowa jest zagrożony **lc_ctype —** kategorii ustawienie ustawień regionalnych, który określa bajtów realizacji i końcowe bajtów znaki wielobajtowe. Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). **_Mbsnbcmp —** funkcja używa bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych. **_Mbsnbcmp_l —** funkcji jest identyczny z tą różnicą, że używa *ustawień regionalnych* parametru zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Jeśli dowolny *ciąg1* lub *ciąg2* jest wskaźnika o wartości null, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcje zwracają **_NLSCMPERROR** i **errno** ustawiono **einval —**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_Unicode — i nie zdefiniowano _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|---------------------------------------|--------------------|-----------------------|
|**_tcsncmp —**|[strncmp —](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|**_mbsnbcmp —**|[wcsncmp —](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|
|**_tcsncmp_l**|[strncmp —](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|**_mbsnbcml**|[wcsncmp —](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbcmp —**|\<mbstring.h>|
|**_mbsnbcmp_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
