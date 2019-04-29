---
title: _stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l
ms.date: 11/04/2016
apiname:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: d27b2128d79d7ff3ab0150e182d494fed52d46ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353842"
---
# <a name="stricmp-wcsicmp-mbsicmp-stricmpl-wcsicmpl-mbsicmpl"></a>_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l

Wykonuje porównania bez uwzględniania ciągów.

> [!IMPORTANT]
> **_mbsicmp —** i **_mbsicmp_l —** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ciągi zakończony wartością null do porównania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana określa relację z *ciąg1* do *ciąg2* w następujący sposób.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*ciąg1* mniej niż *ciąg2*|
|0|*ciąg1* taka sama jak *ciąg2*|
|> 0|*ciąg1* większa *ciąg2*|

W przypadku błędu **_mbsicmp —** zwraca **_NLSCMPERROR**, który jest zdefiniowany w \<string.h > i \<mbstring.h >.

## <a name="remarks"></a>Uwagi

**_Stricmp —** ordinally funkcja porównuje *ciąg1* i *ciąg2* po konwersji każdy znak na małe litery i zwraca wartość wskazującą, ich relacje. **_stricmp —** różni się od **_stricoll —** , **_stricmp —** jedynie wpływ porównania **LC_CTYPE**, określa, jakie znaki są górnej i małe litery. **_Stricoll —** funkcja porównuje ciągi według obu **LC_CTYPE** i **LC_COLLATE** kategorie ustawień regionalnych, który obejmuje zarówno tak, jak i sortowanie kolejność. Aby uzyskać więcej informacji na temat **LC_COLLATE** kategorii, zobacz [setlocale](setlocale-wsetlocale.md) i [kategorie ustawień regionalnych](../../c-runtime-library/locale-categories.md). Wersje tych funkcji, bez **_l** sufiksa używa bieżących ustawień regionalnych dla zachowań zależnych od ustawień regionalnych. Wersje z sufiksem są identyczne, z tą różnicą, że używają w zamian przekazanych ustawień regionalnych. Jeśli nie ustawiono ustawień regionalnych, ustawienia regionalne C jest używany. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

> [!NOTE]
> **_stricmp —** jest odpowiednikiem **_strcmpi —**. Mogą być używane zamiennie, ale **_stricmp —** jest standardów preferowanych.

**_Strcmpi —** funkcji jest odpowiednikiem **_stricmp —** i jest dostępne tylko w trybie zgodności z poprzednimi wersjami.

Ponieważ **_stricmp —** małe porównań, może to spowodować nieoczekiwane zachowanie.

Aby zilustrować, kiedy zamierzone, Zapisz konwersji przez **_stricmp —** wpływa na wynik porównania, założono, że dwa ciągi JOHNSTON i JOHN_HENRY. JOHNSTON ciągu JOHN_HENRY będą uznawane za mniej niż ponieważ "_" ma niższą wartość ASCII niż małe litery S. W rzeczywistości dowolny znak, który ma wartość ASCII między 91 i 96 będą uznawane za mniej niż wszystkie litery.

Jeśli [strcmp —](strcmp-wcscmp-mbscmp.md) funkcja jest używana zamiast **_stricmp —**, JOHN_HENRY będą większe niż JOHNSTON.

**_wcsicmp —** i **_mbsicmp —** są wersjami znaków dwubajtowych i znaków wielobajtowych **_stricmp —**. Argumenty i wartość zwracana przez **_wcsicmp —** są znakami dwubajtowymi ciągów; te z **_mbsicmp —** są ciągami znaków wielobajtowych. **_mbsicmp —** rozpoznaje sekwencje znaków wielobajtowych według bieżącej strony kodowe wielobajtowe i zwraca **_NLSCMPERROR** w przypadku błędu. Aby uzyskać więcej informacji, zobacz [stron kodowych](../../c-runtime-library/code-pages.md). Te trzy funkcje zachowują się identycznie.

**_wcsicmp —** i **wcscmp —** zachowują się identycznie, chyba że **wcscmp —** nie konwertuje argumenty na małe litery, przed ich porównaniem. **_mbsicmp —** i **_mbscmp —** zachowują się identycznie, chyba że **_mbscmp —** nie konwertuje argumenty na małe litery, przed ich porównaniem.

Musisz wywołać [setlocale](setlocale-wsetlocale.md) dla **_wcsicmp —** do pracy z znaki alfabetu łacińskiego 1. Ustawienia regionalne C jest obowiązywały domyślnie, tak, na przykład ä nie zostanie porównany równa Ä. Wywołaj **setlocale** za pomocą dowolnego ustawienia regionalne inne niż ustawienia regionalne C, przed wywołaniem do **_wcsicmp —**. W poniższym przykładzie pokazano sposób **_wcsicmp —** jest wrażliwe na ustawienia regionalne:

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

Alternatywą jest wywołanie [_create_locale, _wcreate_locale](create-locale-wcreate-locale.md) i przekazać obiekt zwrócony ustawień regionalnych jako parametru **_wcsicmp_l —**.

Wszystkie te funkcje sprawdzają poprawność swoich parametrów. Jeśli *ciąg1* lub *ciąg2* wskaźników o wartości null są wywołany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, te funkcje zwracają **_NLSCMPERROR** i ustaw **errno** do **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicmp —**|**_stricmp**|**_mbsicmp**|**_wcsicmp**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_stricmp —**, **_stricmp_l —**|\<string.h>|
|**_wcsicmp —**, **_wcsicmp_l —**|\<Włącz String.h > lub \<wchar.h >|
|**_mbsicmp**, **_mbsicmp_l**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
