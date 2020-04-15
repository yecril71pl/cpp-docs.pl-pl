---
title: _stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l
ms.date: 4/2/2020
api_name:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
- _o__mbsicmp
- _o__mbsicmp_l
- _o__stricmp
- _o__stricmp_l
- _o__wcsicmp
- _o__wcsicmp_l
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 315a86c5cf7e58219bad25f2b6633dd91275c09f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320470"
---
# <a name="_stricmp-_wcsicmp-_mbsicmp-_stricmp_l-_wcsicmp_l-_mbsicmp_l"></a>_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l

Wykonuje porównanie ciągów bez uwzględniania wielkości liter.

> [!IMPORTANT]
> **_mbsicmp** i **_mbsicmp_l** nie mogą być używane w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwracana wartość wskazuje relację *ciągu1* do *ciągu2* w następujący sposób.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*ciąg1* mniej niż *ciąg2*|
|0|*string1* identyczny z *string2*|
|> 0|*ciąg1* większy niż *ciąg2*|

W razie błędu **_mbsicmp** zwraca **_NLSCMPERROR**, który jest \<zdefiniowany w> string.h i \<mbstring.h>.

## <a name="remarks"></a>Uwagi

Funkcja **_stricmp** zwykle porównuje *ciąg1* i *string2* po przekonwertowaniu każdego znaku na małe litery i zwraca wartość wskazującą ich relację. **_stricmp** różni się od **_stricoll** tym, że na **_stricmp** porównanie ma wpływ tylko **LC_CTYPE**, która określa, które znaki są wielkie i małe litery. Funkcja **_stricoll** porównuje ciągi zgodnie z **LC_CTYPE** i **LC_COLLATE** kategorii ustawień regionalnych, która obejmuje zarówno przypadek, jak i kolejność sortowania. Aby uzyskać więcej informacji na temat **kategorii LC_COLLATE,** zobacz [setlocale](setlocale-wsetlocale.md) i [Kategorie ustawień regionalnych](../../c-runtime-library/locale-categories.md). Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych. Wersje z sufiksem są identyczne, z tą różnicą, że używają ustawień regionalnych przekazanych zamiast. Jeśli ustawienia regionalne nie zostały ustawione, używane są ustawienia regionalne języka C. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

> [!NOTE]
> **_stricmp** jest **odpowiednikiem _strcmpi**. Mogą być używane zamiennie, ale **_stricmp** jest preferowanym standardem.

Funkcja **_strcmpi** jest odpowiednikiem **_stricmp** i jest dostępna tylko dla zgodności z powrotem.

Ponieważ **_stricmp** wykonuje małe porównania, może to spowodować nieoczekiwane zachowanie.

Aby zilustrować, kiedy konwersja wielkości liter przez **_stricmp** wpływa na wynik porównania, załóżmy, że masz dwa ciągi JOHNSTON i JOHN_HENRY. Ciąg JOHN_HENRY będzie uważany za mniej niż JOHNSTON, ponieważ "_" ma niższą wartość ASCII niż małe litery S. W rzeczywistości każdy znak, który ma wartość ASCII między 91 i 96 będą uważane za mniej niż jakakolwiek litera.

Jeśli zamiast **_stricmp**jest używana funkcja [strcmp,](strcmp-wcscmp-mbscmp.md) JOHN_HENRY będzie większa niż JOHNSTON.

**_wcsicmp** i **_mbsicmp** są wersjami **_stricmp**o szerokich i wielobajtowych znakach. Argumenty i zwracana wartość **_wcsicmp** są ciągami znaków o szerokich znakach; **_mbsicmp** są ciągami znaków wielobajtowych. **_mbsicmp** rozpoznaje sekwencje znaków wielobajtowych zgodnie z bieżącą wielobajtową stroną kodową i zwraca **_NLSCMPERROR** na błąd. Aby uzyskać więcej informacji, zobacz [Strony kodowe](../../c-runtime-library/code-pages.md). Te trzy funkcje zachowują się identycznie inaczej.

**_wcsicmp** i **wcscmp** zachowują się identycznie, z tą różnicą, że **wcscmp** nie konwertuje swoich argumentów na małe litery przed ich porównaniem. **_mbsicmp** i **_mbscmp** zachowują się identycznie, z tą różnicą, że **_mbscmp** nie konwertuje swoich argumentów na małe litery przed ich porównaniem.

Musisz wywołać [setlocale](setlocale-wsetlocale.md) dla **_wcsicmp** do pracy z łacińskimi 1 znaków. Ustawienia regionalne C obowiązują domyślnie, więc na przykład ä nie będzie porównywany z Ä. Wywołanie **setlocale** z dowolnymi ustawieniami lokalnymi innymi niż ustawienia regionalne C przed wywołaniem **_wcsicmp**. Poniższy przykład pokazuje, jak **_wcsicmp** jest wrażliwy na ustawienia regionalne:

```C
// crt_stricmp_locale.c
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

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

Alternatywą jest [wywołanie _create_locale, _wcreate_locale](create-locale-wcreate-locale.md) i przekazanie zwróconego obiektu ustawień regionalnych jako parametru do **_wcsicmp_l**.

Wszystkie te funkcje sprawdzają poprawność ich parametrów. Jeśli *ciąg1* lub *ciąg2* są wskaźnikami null, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w programie [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcje te zwracają **_NLSCMPERROR** i ustawić **errno** na **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicmp**|**_stricmp**|**_mbsicmp**|**_wcsicmp**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_stricmp** **, _stricmp_l**|\<string.h>|
|**_wcsicmp** **, _wcsicmp_l**|\<string.h> lub \<wchar.h>|
|**_mbsicmp** **, _mbsicmp_l**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll — Funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
