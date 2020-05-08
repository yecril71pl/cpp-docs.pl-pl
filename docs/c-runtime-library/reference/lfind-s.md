---
title: _lfind_s
ms.date: 4/2/2020
api_name:
- _lfind_s
- _o__lfind_s
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
- api-ms-win-crt-utility-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lfind_s
- _lfind_s
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
ms.openlocfilehash: 589a413c9f1fb49fbfe8cd1b5eacb9d452716523
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916505"
---
# <a name="_lfind_s"></a>_lfind_s

Wykonuje wyszukiwanie liniowe dla określonego klucza. Wersja [_lfind](lfind.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
void *_lfind_s(
   const void *key,
   const void *base,
   unsigned int *num,
   size_t size,
   int (__cdecl *compare)(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Obiekt do wyszukania.

*base*<br/>
Wskaźnik do podstawy wyszukiwania danych.

*Liczba*<br/>
Liczba elementów tablicy.

*size*<br/>
Rozmiar elementów tablicy w bajtach.

*porównaniu*<br/>
Wskaźnik do procedury porównania. Pierwszy parametr jest wskaźnikiem *kontekstu* . Drugi parametr jest wskaźnikiem do klucza do wyszukania. Trzeci parametr jest wskaźnikiem do elementu tablicy, który będzie porównywany z kluczem.

*Context*<br/>
Wskaźnik do obiektu, do którego można uzyskać dostęp w funkcji porównywania.

## <a name="return-value"></a>Wartość zwracana

Jeśli klucz zostanie znaleziony, **_lfind_s** zwraca wskaźnik do elementu tablicy w *bazie* , który odpowiada *kluczowi*. Jeśli klucz nie zostanie znaleziony, **_lfind_s** zwraca **wartość null**.

Jeśli do funkcji są przenoszone nieprawidłowe parametry, procedura obsługi nieprawidłowego parametru jest wywoływana, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca **wartość null**.

### <a name="error-conditions"></a>Warunki błędów

|key|base|compare|num|size|errno|
|---------|----------|-------------|---------|----------|-----------|
|**NULL**|ile|ile|ile|ile|**EINVAL**|
|ile|**NULL**|ile|! = 0|ile|**EINVAL**|
|ile|ile|ile|ile|zero|**EINVAL**|
|ile|ile|**NULL**|an|ile|**EINVAL**|

## <a name="remarks"></a>Uwagi

Funkcja **_lfind_s** wykonuje wyszukiwanie liniowe dla *klucza* wartości w tablicy elementów *liczbowych* , każda z bajtów o *szerokości* . W przeciwieństwie do **bsearch_s**, **_lfind_s** nie wymaga sortowania tablicy. Argument *podstawowy* jest wskaźnikiem do podstawy tablicy do przeszukania. Argument *Compare* jest wskaźnikiem do procedury dostarczonej przez użytkownika, która porównuje dwa elementy tablicy, a następnie zwraca wartość określającą ich relację. **_lfind_s** wywołuje procedurę *Compare* jeden lub więcej razy podczas wyszukiwania, przekazując wskaźnik *kontekstu* i wskaźniki do dwóch elementów tablicy dla każdego wywołania. Procedura *Compare* musi porównać elementy, a następnie zwracać wartość różną od zera (co oznacza, że elementy są różne) lub 0 (oznacza to, że elementy są identyczne).

**_lfind_s** jest podobna do **_lfind** z wyjątkiem dodawania wskaźnika *kontekstu* do argumentów funkcji porównania i listy parametrów funkcji. Wskaźnik *kontekstu* może być przydatny, jeśli przeszukiwana struktura danych jest częścią obiektu, a funkcja *porównywania* musi uzyskać dostęp do elementów członkowskich obiektu. Funkcja *Compare* może rzutować wskaźnik void na odpowiedni typ obiektu i uzyskać dostęp do elementów członkowskich tego obiektu. Dodanie parametru *kontekstowego* zapewnia **_lfind_s** bezpieczniejsze, ponieważ można użyć dodatkowego kontekstu, aby uniknąć współużytkowania wątkowości błędów skojarzonych z użyciem zmiennych statycznych w celu udostępnienia danych funkcji *Compare* .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lfind_s**|\<Wyszukaj. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```cpp
// crt_lfind_s.cpp
// This program uses _lfind_s to search a string array,
// passing a locale as the context.
// compile with: /EHsc
#include <stdlib.h>
#include <stdio.h>
#include <search.h>
#include <process.h>
#include <locale.h>
#include <locale>
#include <windows.h>
using namespace std;

// The sort order is dependent on the code page.  Use 'chcp' at the
// command line to change the codepage.  When executing this application,
// the command prompt codepage must match the codepage used here:

#define CODEPAGE_850

#ifdef CODEPAGE_850
// Codepage 850 is the OEM codepage used by the command line,
// so \x00e1 is the German Sharp S

char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };

#define GERMAN_LOCALE "German_Germany.850"

#endif

#ifdef CODEPAGE_1252
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df
   // for the German Sharp S
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };

#define GERMAN_LOCALE "German_Germany.1252"

#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making it vulnerable to thread conflicts
// (if this were a multithreaded program).

int compare( void *pvlocale, const void *str1, const void *str2)
{
    char *s1 = *(char**)str1;
    char *s2 = *(char**)str2;

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(
       s1, s1+strlen(s1),
       s2, s2+strlen(s2) );
}

void find_it( char *key, char *array[], unsigned int num, locale &loc )
{
   char **result = (char **)_lfind_s( &key, array,
                      &num, sizeof(char *), compare, &loc );
   if( result )
      printf( "%s found\n", *result );
   else
      printf( "%s not found\n", key );
}

int main( )
{
   find_it( "weit", array1, sizeof(array1)/sizeof(char*), locale(GERMAN_LOCALE) );
}
```

```Output
weit found
```

## <a name="see-also"></a>Zobacz też

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
