---
title: strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l
ms.date: 4/2/2020
api_name:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
- _o__mbstok_s
- _o__mbstok_s_l
- _o_strtok_s
- _o_wcstok_s
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 52c998f14fee080efc1d288abbba012752757632
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912677"
---
# <a name="strtok_s-_strtok_s_l-wcstok_s-_wcstok_s_l-_mbstok_s-_mbstok_s_l"></a>strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l

Znajduje następny token w ciągu, przy użyciu bieżących ustawień regionalnych lub przekazanych ustawień regionalnych. Te wersje [strtok, _strtok_l, wcstok, _wcstok_l _mbstok _mbstok_l](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbstok_s** i **_mbstok_s_l** nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

unsigned char* _mbstok_s_l(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Ciąg zawierający token lub tokeny do znalezienia.

*Ograniczniki*<br/>
Zestaw znaków ogranicznika do użycia.

*Context*<br/>
Służy do przechowywania informacji o położeniu między wywołaniami funkcji.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do następnego tokenu znalezionego w *str*. Zwraca **wartość null** , jeśli nie znaleziono więcej tokenów. Każde wywołanie modyfikuje *str* , zastępując znak null dla pierwszego ogranicznika, który występuje po zwróconym tokenie.

### <a name="error-conditions"></a>Warunki błędów

|*str*|*Ograniczniki*|*Context*|Wartość zwracana|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**NULL**|ile|wskaźnik do wskaźnika o wartości null|**NULL**|**EINVAL**|
|ile|**NULL**|ile|**NULL**|**EINVAL**|
|ile|ile|**NULL**|**NULL**|**EINVAL**|

Jeśli *str* ma **wartość null** , ale *kontekst* jest wskaźnikiem do prawidłowego wskaźnika kontekstu, nie ma błędu.

## <a name="remarks"></a>Uwagi

**Strtok_s** Rodzina funkcji znajduje następny token w *str*. Zestaw znaków w *ogranicznikach* określa możliwe ograniczniki tokenu, który ma być znaleziony w *str* na bieżącym wywołaniu. **wcstok_s** i **_mbstok_s** są wersjami znaków dwubajtowych i **strtok_s**. Argumenty i wartości zwracane **wcstok_s** i **_wcstok_s_l** są ciągami znaków dwubajtowych; te **_mbstok_s** i **_mbstok_s_l** są ciągami znaków wielobajtowych. Funkcje te zachowują się identycznie w inny sposób.

Ta funkcja sprawdza poprawność swoich parametrów. Gdy wystąpi błąd, jak w tabeli warunków błędu, procedura obsługi nieprawidłowego parametru jest wywoływana, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL** i zwracają **wartość null**.

Przy pierwszym wywołaniu **strtok_s**funkcja pomija wiodące ograniczniki i zwraca wskaźnik do pierwszego tokenu w *str*, kończąc token ze znakiem null. Więcej tokenów można rozbić z pozostałej części *str* przez serię wywołań do **strtok_s**. Każde wywołanie **strtok_s** modyfikuje *str* , wstawiając znak null po tokenie zwróconym przez to wywołanie. Wskaźnik *kontekstu* śledzi, który ciąg jest odczytywany i gdzie w ciągu należy odczytać następny token. Aby odczytać następny token z *str*, wywołaj **Strtok_s** z wartością **null** dla argumentu *str* i przekaż ten sam parametr *kontekstowy* . **Pusty** *str* ciąg jest przyczyną **strtok_s** wyszukiwania następnego tokenu w zmodyfikowanym *str*. Argument *ograniczników* może przyjmować dowolną wartość z jednego wywołania do następnego, aby zestaw ograniczników mógł się różnić.

Ponieważ parametr *kontekstowy* zastępuje bufory statyczne używane w **strtok** i **_strtok_l**, możliwe jest przeanalizowanie dwóch ciągów jednocześnie w tym samym wątku.

Wartość wyjściowa jest zależna od ustawienia ustawienia kategorii **LC_CTYPE** ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md).

Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych wątku dla tego zachowania zależnego od ustawień regionalnych. Wersje z sufiksem **_l** są identyczne, z tą różnicą, że zamiast nich używają ustawień regionalnych określonych przez parametr *locale* . Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtok_s**|\<> String. h|
|**_strtok_s_l**|\<> String. h|
|**wcstok_s**,<br />**_wcstok_s_l**|\<ciąg. h> lub \<WCHAR. h>|
|**_mbstok_s**,<br />**_mbstok_s_l**|\<mbstring. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|\_Nie zdefiniowano MBCS UNICODE & \_|\_MBCS zdefiniowany|_UNICODE zdefiniowano|
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

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Ustawienie](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
