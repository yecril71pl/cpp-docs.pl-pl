---
title: strtok_s —, _strtok_s_l —, wcstok_s —, _wcstok_s_l —, _mbstok_s —, _mbstok_s_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 467184acd7ef78ee52f1605d23f2d3b80e6adb83
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="strtoks-strtoksl-wcstoks-wcstoksl-mbstoks-mbstoksl"></a>strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l

Znajduje następny token w ciągu, używając bieżących ustawień regionalnych lub ustawień regionalnych, który jest przekazywany w. Te wersje programu [strtok —, _strtok_l —, wcstok —, _wcstok_l —, _mbstok —, _mbstok_l —](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbstok_s —** i **_mbstok_s_l —** nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Używany do przechowywania informacji o położeniu między wywołania funkcji.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do następnego tokenu w *str*. Zwraca **NULL** gdy znajdują się żadnych kolejnych tokenów. Każde wywołanie modyfikuje *str* podstawiając znak null dla pierwszego ogranicznika występujący po zwrócony tokenu.

### <a name="error-conditions"></a>Warunki błędów

|*str*|*ograniczniki*|*Kontekst*|Wartość zwracana|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**NULL**|wszystkie|wskaźnik do wskaźnika o wartości null|**NULL**|**EINVAL —**|
|wszystkie|**NULL**|wszystkie|**NULL**|**EINVAL —**|
|wszystkie|wszystkie|**NULL**|**NULL**|**EINVAL —**|

Jeśli *str* jest **NULL** , ale *kontekstu* wskaźnik do wskaźnika prawidłowego kontekstu nie było błędu.

## <a name="remarks"></a>Uwagi

**Strtok_s —** rodziny funkcji znajduje następny token w *str*. Zestaw znaków *ograniczniki* określa możliwe ograniczniki tokenu, który ma zostać odnaleziona w *str* w bieżącym wywołaniu. **wcstok_s —** i **_mbstok_s —** znaków dwubajtowych i znaków wielobajtowych wersji **strtok_s —**. Argumentów i wartości zwracanych z **wcstok_s —** i **_wcstok_s_l —** są znaków dwubajtowych ciągi; tych **_mbstok_s —** i **_mbstok_s_l —** są ciągami znaków wielobajtowych. Funkcje te działają tak samo w przeciwnym razie wartość.

Ta funkcja weryfikuje jego parametrów. Jeśli wystąpi błąd, tak jak w tabeli błędów program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji **errno** do **einval —** i zwracać **NULL**.

W pierwszym wywołaniu **strtok_s —** funkcja pomija ograniczniki początkowych i zwraca wskaźnik do pierwszym tokenie w *str*, przerywanie token znakiem null. Więcej tokenów mogą być podzielone poza pozostałej części *str* serii wywołań **strtok_s —**. Każde wywołanie **strtok_s —** modyfikuje *str* wstawiając znak null po tokenie zwracanych przez tego wywołania. *Kontekstu* wskaźnika przechowuje informacje o ciąg, który jest odczytywany i gdzie w ciągu następnej token jest do odczytu. Można odczytać następnego tokenu z *str*, wywołaj **strtok_s —** z **NULL** wartość *str* argumentu i przekazywać taki sam  *kontekst* parametru. **NULL** *str* powoduje, że argument **strtok_s —** aby wyszukać następny token w modyfikacji *str*. *Ograniczniki* argument może zająć dowolną wartość z jednego wywołania do następnego tak, aby zestaw ograniczników może się różnić.

Ponieważ *kontekstu* parametru zastępuje buforów statyczne, używane w **strtok —** i **_strtok_l —**, można przeanalizować dwa ciągi jednocześnie w tym samym wątku.

Wartość wyjściowa jest zagrożony ustawienie **lc_ctype —** ustawienie kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez **_l** sufiks Użyj bieżącego ustawienia regionalne wątku tego zachowania zależnych od ustawień regionalnych. Wersje z **_l** sufiks są identyczne z tą różnicą, że zamiast tego użyć *ustawień regionalnych* parametru. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s —**,<br />**_wcstok_s_l**|\<String.h > lub \<wchar.h >|
|**_mbstok_s —**,<br />**_mbstok_s_l**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|\_UNICODE & \_nie zdefiniowano MBCS|\_Definicja MBCS|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok_s —**|**strtok_s**|**_mbstok_s**|**wcstok_s**|
|**_tcstok_s_l —**|**_strtok_s_l**|**_mbstok_s_l**|**_wcstok_s_l**|

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
