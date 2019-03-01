---
title: strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l
ms.date: 11/04/2016
apiname:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _tcstok_s_l
- _wcstok_s_l
- _tcstok_s
- _mbstok_s_l
- strtok_s
- wcstok_s
- _mbstok_s
- _strtok_s_l
helpviewer_keywords:
- _strtok_s_l function
- _mbstok_s_l function
- strings [C++], searching
- mbstok_s_l function
- wcstok_s_l function
- _wcstok_s_l function
- _tcstok_s function
- _tcstok_s_l function
- strtok_s_l function
- wcstok_s function
- tokens, finding in strings
- mbstok_s function
- _mbstok_s function
- strtok_s function
ms.assetid: 7696c972-f83b-4617-8c82-95973e9fdb46
ms.openlocfilehash: 24a945742f3db82e41f662a337eef1f79ef13bd6
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210591"
---
# <a name="strtoks-strtoksl-wcstoks-wcstoksl-mbstoks-mbstoksl"></a>strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l

Znajduje następny token w ciągu, przy użyciu bieżących ustawień regionalnych lub przekazanych ustawień regionalnych. Te wersje [strtok —, _strtok_l —, wcstok —, _wcstok_l —, _mbstok —, _mbstok_l —](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbstok_s —** i **_mbstok_s_l —** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
char* strtok_s(
   char* str,
   const char* delimiters,
   char** context
);

char* _strtok_s_l(
   char* str,
   const char* delimiters,
   char** context,
   _locale_t locale
);

wchar_t* wcstok_s(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context
);

wchar_t *_wcstok_s_l(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context,
   _locale_t locale
);

unsigned char* _mbstok_s(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context
);

unsigned char* _mbstok_s(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Ciąg zawierający token lub tokeny do znalezienia.

*ograniczniki*<br/>
Zestaw znaków ogranicznika do użycia.

*Kontekst*<br/>
Używane do przechowywania informacji pozycji między wywołań funkcji.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do następnego tokenu w *str*. Zwraca **NULL** gdy znajdują się żadnych kolejnych tokenów. Każde wywołanie modyfikuje *str* , zastępując znak null w poszukiwaniu ogranicznika pierwszy, która występuje po zwrócony token.

### <a name="error-conditions"></a>Warunki błędów

|*str*|*ograniczniki*|*Kontekst*|Wartość zwracana|**numer błędu**|
|----------------|------------------|---------------|------------------|-------------|
|**NULL**|Wszystkie|wskaźnik do wskaźnika o wartości null|**NULL**|**EINVAL**|
|Wszystkie|**NULL**|Wszystkie|**NULL**|**EINVAL**|
|Wszystkie|Wszystkie|**NULL**|**NULL**|**EINVAL**|

Jeśli *str* jest **NULL** , ale *kontekstu* jest wskaźnikiem do wskaźnika prawidłowego kontekstu nie ma błędów.

## <a name="remarks"></a>Uwagi

**Strtok_s —** rodzinę funkcji znajduje następny token w *str*. Zestaw znaków *ograniczniki* określa ograniczniki możliwe tokenu, który ma zostać odnaleziona w *str* w bieżącym wywołaniu. **wcstok_s —** i **_mbstok_s —** są wersjami znaków dwubajtowych i znaków wielobajtowych **strtok_s —**. Argumenty i wartości zwracane **wcstok_s —** i **_wcstok_s_l —** są znakami dwubajtowymi ciągów; te z **_mbstok_s —** i **_mbstok_s_l —** są ciągami znaków wielobajtowych. Funkcje te zachowują się identycznie.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli wystąpi błąd, tak jak w tabeli błędów, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają **NULL**.

W pierwszym wywołaniu **strtok_s —** funkcja pomija wiodących ograniczniki i zwraca wskaźnik do pierwszego token w *str*, przerywa token znakiem null. Kolejnych tokenów można zaburzyć poza pozostałą część *str* przez szereg wywołań do **strtok_s —**. Każde wywołanie **strtok_s —** modyfikuje *str* przez wstawienie znaku null po tokenowi zwróconemu przez to wywołanie. *Kontekstu* śledzi informacje o wskaźnik ciągu, który jest odczytywany, gdzie w ciągu następnego tokenu jest do odczytu. Można odczytać następnego tokenu z *str*, wywołaj **strtok_s —** z **o wartości NULL** wartość *str* argument i przekazać takie same  *kontekst* parametru. **NULL** *str* powoduje, że argument **strtok_s —** aby wyszukać następny token w zmodyfikowanego *str*. *Ograniczniki* argument może przyjąć dowolną wartość z jednego wywołania do następnego tak, aby zestaw ograniczników mogą się różnić.

Ponieważ *kontekstu* parametr zastępuje statyczne buforów używane w **strtok —** i **_strtok_l —**, można przeanalizować dwa ciągi jednocześnie w tym samym wątku.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, bez **_l** sufiksa używa bieżących ustawień regionalnych wątku tego zachowania zależnego od ustawień regionalnych. Wersje **_l** sufiksem są identyczne, z tą różnicą, że używają w zamian *ustawień regionalnych* parametru. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s —**,<br />**_wcstok_s_l**|\<Włącz String.h > lub \<wchar.h >|
|**_mbstok_s**,<br />**_mbstok_s_l**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|\_UNICODE & \_MBCS niezdefiniowana|\_MBCS zdefiniowany|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok_s**|**strtok_s**|**_mbstok_s**|**wcstok_s**|
|**_tcstok_s_l**|**_strtok_s_l**|**_mbstok_s_l**|**_wcstok_s_l**|

## <a name="example"></a>Przykład

```C
// crt_strtok_s.c
// In this program, a loop uses strtok_s
// to print all the tokens (separated by commas
// or blanks) in two strings at the same time.

#include <string.h>
#include <stdio.h>

char string1[] =
    "A string\tof ,,tokens\nand some  more tokens";
char string2[] =
    "Another string\n\tparsed at the same time.";
char seps[]   = " ,\t\n";
char *token1 = NULL;
char *token2 = NULL;
char *next_token1 = NULL;
char *next_token2 = NULL;

int main(void)
{
    printf("Tokens:\n");

    // Establish string and get the first token:
    token1 = strtok_s(string1, seps, &next_token1);
    token2 = strtok_s(string2, seps, &next_token2);

    // While there are tokens in "string1" or "string2"
    while ((token1 != NULL) || (token2 != NULL))
    {
        // Get next token:
        if (token1 != NULL)
        {
            printf(" %s\n", token1);
            token1 = strtok_s(NULL, seps, &next_token1);
        }
        if (token2 != NULL)
        {
            printf("        %s\n", token2);
            token2 = strtok_s(NULL, seps, &next_token2);
        }
    }
}
```

```Output
Tokens:
A
        Another
string
        string
of
        parsed
tokens
        at
and
        the
some
        same
more
        time.
tokens
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
