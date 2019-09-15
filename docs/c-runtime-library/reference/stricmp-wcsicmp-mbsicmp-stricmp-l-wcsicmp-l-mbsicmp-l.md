---
title: _stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l
ms.date: 11/04/2016
api_name:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ftcsicmp
- _stricmp
- wcsicmp_l
- _wcsicmp
- _tcsicmp
- _strcmpi
- stricmp_l
- _mbsicmp
- _fstricmp
- mbsicmp_l
- mbsicmp
helpviewer_keywords:
- _wcsicmp function
- _stricmp_l function
- fstricmp function
- _tcsicmp function
- ftcsicmp function
- string comparison [C++], lowercase
- _wcsicmp_l function
- _fstricmp function
- strings [C++], comparing
- mbsicmp function
- _ftcsicmp function
- _mbsicmp_l function
- wcsicmp_l function
- _stricmp function
- _mbsicmp function
- tcsicmp function
- stricmp_l function
- mbsicmp_l function
- _strcmpi function
ms.assetid: 0e1ee515-0d75-435a-a445-8875d4669b50
ms.openlocfilehash: 108a3c572174be5048d0bba48a4da0f4a735f458
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940682"
---
# <a name="_stricmp-_wcsicmp-_mbsicmp-_stricmp_l-_wcsicmp_l-_mbsicmp_l"></a>_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l

Wykonuje porównanie ciągów bez uwzględniania wielkości liter.

> [!IMPORTANT]
> **_mbsicmp** i **_mbsicmp_l** nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _stricmp(
   const char *string1,
   const char *string2
);
int _wcsicmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbsicmp(
   const unsigned char *string1,
   const unsigned char *string2
);
int _stricmp_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int _wcsicmp_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbsicmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*ciąg1*, *ciąg2*<br/>
Ciągi zakończone wartością null do porównania.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana wskazuje relację od *ciąg1* do *ciąg2* w następujący sposób.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*ciąg1* mniejszy niż *ciąg2*|
|0|*ciąg1* identyczny z *ciąg2*|
|> 0|*ciąg1* większy niż *ciąg2*|

W przypadku błędu **_mbsicmp** zwraca **_NLSCMPERROR**, który jest zdefiniowany w \<String. h > i \<mbstring. h >.

## <a name="remarks"></a>Uwagi

Funkcja **_stricmp** w liczbie porządkowej porównuje wartości *ciąg1* i *ciąg2* po przeprowadzeniu konwersji każdego znaku na małe litery i zwraca wartość wskazującą swoją relację. **_stricmp** różni się od **_stricoll** w tym, że porównanie **_Stricmp** ma wpływ tylko na **LC_CTYPE**, który określa, które znaki są wielkie i małe litery. Funkcja **_stricoll** porównuje ciągi zgodnie z kategoriami **LC_CTYPE** i **LC_COLLATE** ustawień regionalnych, które obejmują zarówno kolejność, jak i porządek sortowania. Aby uzyskać więcej informacji na temat kategorii **LC_COLLATE** , zobacz sekcję [setlocales](setlocale-wsetlocale.md) i [locale](../../c-runtime-library/locale-categories.md). Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla zachowań zależnych od ustawień regionalnych. Wersje z sufiksem są identyczne, z tą różnicą, że w zamian korzystają z przekazaną ustawieniami regionalnymi. Jeśli ustawienia regionalne nie zostały ustawione, używane są ustawienia regionalne języka C. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

> [!NOTE]
> **_stricmp** jest odpowiednikiem **_strcmpi**. Mogą być używane zamiennie, ale **_stricmp** jest standardem preferowanym.

Funkcja **_strcmpi** jest równoważna z **_stricmp** i jest udostępniana tylko w celu zapewnienia zgodności z poprzednimi wersjami.

Ponieważ **_stricmp** wykonuje małe porównania, może to spowodować nieoczekiwane zachowanie.

Aby zilustrować, kiedy konwersja wielkości liter przez **_stricmp** ma wpływ na wynik porównania, Załóżmy, że istnieją dwa ciągi Johnston i JOHN_HENRY. Ciąg JOHN_HENRY będzie traktowany jako mniej niż JOHNSTON, ponieważ "_" ma niższą wartość ASCII niż mała litera S. W rzeczywistości każdy znak, który ma wartość ASCII z zakresu od 91 do 96, będzie traktowany jako mniej niż jakakolwiek litera.

Jeśli funkcja [strcmp](strcmp-wcscmp-mbscmp.md) jest używana zamiast **_stricmp**, JOHN_HENRY będzie większa niż Johnston.

**_wcsicmp** i **_mbsicmp** są wersjami znaków dwubajtowych i znakami wieloznacznymi **_stricmp**. Argumenty i wartość zwracana przez **_wcsicmp** są ciągami znaków dwubajtowych; te z **_mbsicmp** są ciągami znaków wielobajtowych. **_mbsicmp** rozpoznaje sekwencje znaków wielobajtowych zgodnie z bieżącą stroną kodową wielobajtowego i zwraca **_NLSCMPERROR** w przypadku błędu. Aby uzyskać więcej informacji, zobacz [stronę kodową](../../c-runtime-library/code-pages.md). Te trzy funkcje zachowują się identycznie w inny sposób.

**_wcsicmp** i **wcscmp** zachowują się identycznie, z tą różnicą, że **wcscmp** nie konwertują swoich argumentów na małe przed ich porównaniem. **_mbsicmp** i **_mbscmp** zachowują się identycznie, z tą różnicą, że **_mbscmp** nie konwertują swoich argumentów na małe przed ich porównaniem.

Aby można było korzystać z znaków łacińskich 1, należy wywołać metodę [setlocaling](setlocale-wsetlocale.md) for **_wcsicmp** . Ustawienia regionalne języka C są stosowane domyślnie, więc na przykład ä nie będzie porównywane z Ä. Wywołaj metodę **setlocals** z dowolnymi ustawieniami regionalnymi innymi niż ustawienia regionalne języka C przed wywołaniem do **_wcsicmp**. Poniższy przykład demonstruje, jak **_wcsicmp** jest wrażliwy na ustawienia regionalne:

```C
// crt_stricmp_locale.c
#include <string.h>
#include <stdio.h>
#include <locale.h>

int main() {
   setlocale(LC_ALL,"C");   // in effect by default
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare fails
   setlocale(LC_ALL,"");
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare succeeds
}
```

Alternatywą jest wywołanie [_create_locale, _wcreate_locale](create-locale-wcreate-locale.md) i przekazanie zwróconego obiektu ustawień regionalnych jako parametru do **_wcsicmp_l**.

Wszystkie te funkcje sprawdzają poprawność swoich parametrów. Jeśli *ciąg1* lub *ciąg2* ma wskaźniki null, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, te funkcje zwracają **_NLSCMPERROR** i ustawiają **errno** na **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicmp**|**_stricmp**|**_mbsicmp**|**_wcsicmp**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_stricmp**, **_stricmp_l**|\<string.h>|
|**_wcsicmp**, **_wcsicmp_l**|\<ciąg. h > lub \<WCHAR. h >|
|**_mbsicmp**, **_mbsicmp_l**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_stricmp.c

#include <string.h>
#include <stdio.h>
#include <stdlib.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown dog jumps over the lazy fox";

int main( void )
{
   char tmp[20];
   int result;

   // Case sensitive
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );
   result = strcmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
   The quick brown dog jumps over the lazy fox
   The QUICK brown dog jumps over the lazy fox

   strcmp:   String 1 is greater than string 2
   _stricmp:  String 1 is equal to string 2
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
