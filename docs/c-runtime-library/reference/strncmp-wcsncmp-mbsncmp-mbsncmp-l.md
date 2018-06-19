---
title: strncmp —, wcsncmp —, _mbsncmp —, _mbsncmp_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- strncmp
- _mbsncmp
- wcsncmp
- _mbsncmp_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ftcsnccmp
- _ftcsncmp
- _tcsncmp
- _tcsnccmp
- strncmp
- _mbsncmp
- wcsncmp
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a64d7248151287f4f2af38e666db62f9a15d833f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417356"
---
# <a name="strncmp-wcsncmp-mbsncmp-mbsncmpl"></a>strncmp, wcsncmp, _mbsncmp, _mbsncmp_l

Porównano do określonej liczby znaków dwóch ciągów.

> [!IMPORTANT]
> **_mbsncmp —** i **_mbsncmp_l —** nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Wartości zwracanej wskazuje relacja podciągów *ciąg1* i *ciąg2* w następujący sposób.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*ciąg1* podciąg mniej niż *ciąg2* podciągu|
|0|*ciąg1* podciąg taki sam jak *ciąg2* podciągu|
|> 0|*ciąg1* podciąg większe *ciąg2* podciągu|

Parametr błędu sprawdzania poprawności **_mbsncmp —** i **_mbsncmp_l —** zwracać **_NLSCMPERROR**, która jest zdefiniowana w \<string.h > i \< mbstring.h >.

## <a name="remarks"></a>Uwagi

**Strncmp —** funkcja przeprowadza porównanie liczby porządkowej co najwyżej pierwszego *liczba* znaków *ciąg1* i *ciąg2* i Zwraca wartość wskazującą relacji między podciągów. **strncmp —** jest rozróżniana wielkość liter wersja **_strnicmp —**. **wcsncmp —** i **_mbsncmp —** z uwzględnieniem wielkości liter wersji **_wcsnicmp —** i **_mbsnicmp —**.

**wcsncmp —** i **_mbsncmp —** znaków dwubajtowych i znaków wielobajtowych wersji **strncmp —**. Argumenty **wcsncmp —** są znaków dwubajtowych ciągi; tych **_mbsncmp —** są ciągami znaków wielobajtowych. **_mbsncmp —** rozpoznaje wielobajtowych sekwencji znaków zgodnie ze strony kodowe wielobajtowe i zwraca **_NLSCMPERROR** w przypadku wystąpienia błędu.

Ponadto **_mbsncmp —** i **_mbsncmp_l —** sprawdza poprawność parametrów. Jeśli *ciąg1* lub *ciąg2* wskaźnika o wartości null, jest program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **_mbsncmp —** i **_mbsncmp_l —** zwracać **_NLSCMPERROR** i ustaw **errno** do  **Einval —**. **strncmp —** i **wcsncmp —** nie weryfikują ich parametrów. Funkcje te działają tak samo w przeciwnym razie wartość.

Zachowanie porównanie **_mbsncmp —** i **_mbsncmp_l —** zależy od ustawienia **lc_ctype —** ustawienie kategorii ustawień regionalnych. Kontroluje do wykrywania bajty wiodące i końcowe znaki wielobajtowe. Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). **_Mbsncmp —** funkcja używa bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych. **_Mbsncmp_l —** funkcji jest identyczny z tą różnicą, że używa *ustawień regionalnych* parametru zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md). Jeśli ustawienia regionalne są jednobajtowe ustawień regionalnych, działanie tych funkcji jest taki sam jak **strncmp —**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccmp —**|**strncmp —**|**_mbsncmp —**|**wcsncmp —**|
|**_tcsncmp —**|**strncmp —**|**_mbsnbcmp —**|**wcsncmp —**|
|**_tccmp**|Map — makro lub wewnętrznej funkcji|**_mbsncmp —**|Map — makro lub wewnętrznej funkcji|
|**Nie dotyczy**|**Nie dotyczy**|**_mbsncmp_l —**|**Nie dotyczy**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strncmp —**|\<string.h>|
|**wcsncmp —**|\<String.h > lub \<wchar.h >|
|**_mbsncmp —**, **_mbsncmp_l —**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
