---
title: strncmp, wcsncmp, _mbsncmp, _mbsncmp_l
ms.date: 11/04/2016
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
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: 8f022dec6c161814ade5c6be5aaccfcd239a4af4
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210916"
---
# <a name="strncmp-wcsncmp-mbsncmp-mbsncmpl"></a>strncmp, wcsncmp, _mbsncmp, _mbsncmp_l

Porównano do określonej liczby znaków dwa ciągi.

> [!IMPORTANT]
> **_mbsncmp —** i **_mbsncmp_l —** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ciągi znaków do porównania.

*Liczba*<br/>
Liczba znaków do porównania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana określa relację z podciągów *ciąg1* i *ciąg2* w następujący sposób.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*ciąg1* podciąg mniejszy niż *ciąg2* podciąg|
|0|*ciąg1* podciąg identyczny z *ciąg2* podciąg|
|> 0|*ciąg1* podciąg większy niż *ciąg2* podciąg|

Na błąd sprawdzania poprawności parametru **_mbsncmp —** i **_mbsncmp_l —** zwracają **_NLSCMPERROR**, który jest zdefiniowany w \<string.h > i \< mbstring.h >.

## <a name="remarks"></a>Uwagi

**Strncmp —** funkcja wykonuje porównanie porządkowe, co najwyżej pierwsze *liczba* znaki w *ciąg1* i *ciąg2* i Zwraca wartość określającą relację pomiędzy podciągami. **strncmp —** jest rozróżniana wielkość liter wersją **_strnicmp —**. **wcsncmp —** i **_mbsncmp —** jest rozróżniana wielkość liter wersje **_wcsnicmp —** i **_mbsnicmp —**.

**wcsncmp —** i **_mbsncmp —** są wersjami znaków dwubajtowych i znaków wielobajtowych **strncmp —**. Argumenty **wcsncmp —** są znakami dwubajtowymi ciągów; te z **_mbsncmp —** są ciągami znaków wielobajtowych. **_mbsncmp —** rozpoznaje sekwencje znaków wielobajtowych według stronę kodu wielobajtowego i zwraca **_NLSCMPERROR** w przypadku błędu.

Ponadto **_mbsncmp —** i **_mbsncmp_l —** sprawdzają poprawność parametrów. Jeśli *ciąg1* lub *ciąg2* jest pustym wskaźnikiem, wywoływany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **_mbsncmp —** i **_mbsncmp_l —** zwracają **_NLSCMPERROR** i ustaw **errno** do  **EINVAL**. **strncmp —** i **wcsncmp —** nie sprawdzają poprawność swoich parametrów. Funkcje te zachowują się identycznie.

Zachowanie porównania **_mbsncmp —** i **_mbsncmp_l —** jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych. Ta opcja kontroluje wykrywanie początkowe i końcowe bajtów znaków wielobajtowych. Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). **_Mbsncmp —** funkcji używa bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych. **_Mbsncmp_l —** funkcja jest identyczna, z tą różnicą, że używa *ustawień regionalnych* parametru zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md). Jeśli ustawienia regionalne są jednobajtowe ustawień regionalnych, zachowanie tych funkcji jest taka sama jak **strncmp —**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccmp —**|**strncmp**|**_mbsncmp**|**wcsncmp —**|
|**_tcsncmp —**|**strncmp**|**_mbsnbcmp**|**wcsncmp —**|
|**_tccmp**|Mapy i makro lub funkcja śródwierszowa|**_mbsncmp**|Mapy i makro lub funkcja śródwierszowa|
|**Nie dotyczy**|**Nie dotyczy**|**_mbsncmp_l**|**Nie dotyczy**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strncmp**|\<string.h>|
|**wcsncmp —**|\<Włącz String.h > lub \<wchar.h >|
|**_mbsncmp**, **_mbsncmp_l**|\<mbstring.h>|

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
