---
title: _lfind_s
ms.date: 11/04/2016
apiname:
- _lfind_s
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 08c04d9d1ca69998d54304c96468298013907179
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62286430"
---
# <a name="lfinds"></a>_lfind_s

Wykonuje wyszukiwanie liniowe dla określonego klucza. Wersja [_lfind —](lfind.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Klucz*<br/>
Obiekt do wyszukania.

*base*<br/>
Wskaźnik do bazy danych wyszukiwania.

*Numer*<br/>
Liczba elementów tablicy.

*Rozmiar*<br/>
Rozmiar elementów tablicy, w bajtach.

*compare*<br/>
Wskaźnik do procedury porównania. Pierwszy parametr jest *kontekstu* wskaźnika. Drugi parametr jest wskaźnikiem do klucza dla wyszukiwania. Trzeci parametr jest wskaźnik do elementu tablicy, który można porównać z kluczem.

*Kontekst*<br/>
Wskaźnik do obiektu, który może być uzyskiwany w funkcji porównywania.

## <a name="return-value"></a>Wartość zwracana

Jeśli klucz zostanie znaleziony, **_lfind_s —** zwraca wskaźnik do elementu tablicy, od *podstawowy* odpowiadający *klucz*. Jeśli klucz nie zostanie znaleziony, **_lfind_s —** zwraca **NULL**.

Jeśli nieprawidłowe parametry są przekazywane do funkcji, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca **NULL**.

### <a name="error-conditions"></a>Warunki błędów

|klawisz|base|compare|Liczba|size|errno|
|---------|----------|-------------|---------|----------|-----------|
|**NULL**|Wszystkie|Wszystkie|Wszystkie|Wszystkie|**EINVAL**|
|Wszystkie|**NULL**|Wszystkie|!= 0|Wszystkie|**EINVAL**|
|Wszystkie|Wszystkie|Wszystkie|Wszystkie|zero|**EINVAL**|
|Wszystkie|Wszystkie|**NULL**|Usługi|Wszystkie|**EINVAL**|

## <a name="remarks"></a>Uwagi

**_Lfind_s —** funkcja wykonuje wyszukiwanie liniowe dla wartości *klucz* tablicę *numer* elementów, z których każdy z *szerokość* bajtów. W odróżnieniu od **bsearch_s —**, **_lfind_s —** nie wymaga tablicy, która ma zostać posortowana. *Podstawowy* argument jest wskaźnikiem do podstawy tablicy, który ma być przeszukiwany. *Porównania* argument jest wskaźnikiem do procedury dostarczone przez użytkownika, która porównuje dwa elementy tablicy, a następnie zwraca wartość określającą, ich relacje. **_lfind_s —** wywołania *porównania* rutynowych jeden lub więcej razy podczas wyszukiwania, przekazując *kontekstu* wskaźnik i wskaźniki do dwóch elementów tablicy przy każdym wywołaniu. *Porównania* procedury należy porównać elementów, a następnie zwraca wartość różną od zera (co oznacza że elementy są różne) lub od 0 (co oznacza, że elementy są identyczne).

**_lfind_s —** przypomina **_lfind —** z wyjątkiem dodawania *kontekstu* wskaźnik do argumentów funkcji porównywania i lista parametrów funkcji. *Kontekstu* wskaźnik może być przydatne, jeśli struktura wyszukiwanych danych jest częścią obiektu i *porównania* funkcji ma dostęp do elementów członkowskich obiektu. *Porównania* funkcji można rzutować wskaźnika void do odpowiedniego obiektu typu i dostęp do elementów członkowskich tego obiektu. Dodanie *kontekstu* sprawia, że parametr **_lfind_s —** bezpieczniejsze, ponieważ dodatkowy kontekst można uniknąć błędów współużytkowania wątkowości, związanych z użyciem statyczne zmienne, aby udostępnić dane *porównania* funkcji.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lfind_s**|\<Search.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
