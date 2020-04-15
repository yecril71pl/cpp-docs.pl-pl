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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 8f2983bee93c623eb936ed12422134281418076b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342186"
---
# <a name="_lfind_s"></a>_lfind_s

Wykonuje wyszukiwanie liniowe określonego klucza. Wersja [_lfind](lfind.md) z ulepszeniami zabezpieczeń, jak opisano w [obszarze Funkcje zabezpieczeń w crt](../../c-runtime-library/security-features-in-the-crt.md).

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

*key*<br/>
Obiekt do wyszukania.

*base*<br/>
Wskaźnik do podstawy danych wyszukiwania.

*numer*<br/>
Liczba elementów tablicy.

*Rozmiar*<br/>
Rozmiar elementów tablicy w bajtach.

*Porównać*<br/>
Wskaźnik do procedury porównania. Pierwszym parametrem jest wskaźnik *kontekstu.* Drugi parametr jest wskaźnikiem do klucza do wyszukiwania. Trzeci parametr jest wskaźnikiem do elementu tablicy, który ma być porównywany z kluczem.

*Kontekście*<br/>
Wskaźnik do obiektu, który może być dostępny w funkcji porównania.

## <a name="return-value"></a>Wartość zwracana

Jeśli klucz zostanie znaleziony, **_lfind_s** zwraca wskaźnik do elementu tablicy u *podstawy,* który pasuje do *klucza*. Jeśli klucz nie zostanie znaleziony, **_lfind_s** zwraca **wartość NULL**.

Jeśli nieprawidłowe parametry są przekazywane do funkcji, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **Wartość EINVAL,** a funkcja zwraca **wartość NULL**.

### <a name="error-conditions"></a>Warunki błędu

|key|base|compare|num|size|Errno|
|---------|----------|-------------|---------|----------|-----------|
|**Null**|Wszelki|Wszelki|Wszelki|Wszelki|**Einval**|
|Wszelki|**Null**|Wszelki|!= 0|Wszelki|**Einval**|
|Wszelki|Wszelki|Wszelki|Wszelki|zero|**Einval**|
|Wszelki|Wszelki|**Null**|an|Wszelki|**Einval**|

## <a name="remarks"></a>Uwagi

Funkcja **_lfind_s** wykonuje liniowe wyszukiwanie *klucza* wartości w tablicy elementów *liczbowych,* z których każdy bajtów *szerokości.* W przeciwieństwie do **bsearch_s** **_lfind_s** nie wymaga sortowania tablicy. Argument *podstawowy* jest wskaźnikiem do podstawy tablicy, która ma zostać przeszukana. Argument *porównania* jest wskaźnikiem do procedury dostarczonej przez użytkownika, która porównuje dwa elementy tablicy, a następnie zwraca wartość określającą ich relację. **_lfind_s** wywołuje *rutynowe porównywanie* jeden lub więcej razy podczas wyszukiwania, przekazując wskaźnik *kontekstu* i wskaźniki do dwóch elementów tablicy w każdym wywołaniu. Procedura *porównywania* musi porównać elementy, a następnie zwrócić różną wartość (co oznacza, że elementy są różne) lub 0 (co oznacza, że elementy są identyczne).

**_lfind_s** jest podobny do **_lfind** z wyjątkiem dodania *wskaźnika kontekstu* do argumentów funkcji porównania i listy parametrów funkcji. Wskaźnik *kontekstu* może być przydatne, jeśli przeszukiwana struktura danych jest częścią obiektu i *funkcja porównania* musi uzyskać dostęp do elementów członkowskich obiektu. Funkcja *porównywania* może rzutować wskaźnik void do odpowiedniego typu obiektu i uzyskać dostęp do elementów członkowskich tego obiektu. Dodanie *parametru kontekstu* sprawia, **że _lfind_s** bardziej bezpieczne, ponieważ dodatkowy kontekst może służyć do uniknięcia błędów reentrancy skojarzone z przy użyciu zmiennych statycznych, aby udostępnić dane do funkcji *porównania.*

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lfind_s**|\<> search.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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
