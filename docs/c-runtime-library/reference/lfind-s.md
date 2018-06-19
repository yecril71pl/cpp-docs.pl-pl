---
title: _lfind_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 963b657a009f7376a17706b4ac1e5fb4e8b69237
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404821"
---
# <a name="lfinds"></a>_lfind_s

Wykonuje wyszukiwanie liniowe dla określonego klucza. Wersja [_lfind —](lfind.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Rozmiar elementów tablicy w bajtach.

*Porównaj*<br/>
Wskaźnik do porównania procedury. Pierwszym parametrem jest *kontekstu* wskaźnika. Drugi parametr jest wskaźnik do klucza dla wyszukiwania. Trzeci parametr jest wskaźnik do elementu tablicy ma zostać porównane z kluczem.

*Kontekst*<br/>
Wskaźnik do obiektu, który mogą być używane w funkcji porównania.

## <a name="return-value"></a>Wartość zwracana

Jeśli klucz zostanie znaleziony, **_lfind_s —** zwraca wskaźnik do elementu tablicy w *podstawowej* odpowiadającego *klucza*. Jeśli klucz nie zostanie znaleziony, **_lfind_s —** zwraca **NULL**.

Jeśli nieprawidłowe parametry są przekazywane do funkcji, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i funkcja zwraca **NULL**.

### <a name="error-conditions"></a>Warunki błędów

|klawisz|base|compare|NUM|size|errno|
|---------|----------|-------------|---------|----------|-----------|
|**NULL**|wszystkie|wszystkie|wszystkie|wszystkie|**EINVAL —**|
|wszystkie|**NULL**|wszystkie|!= 0|wszystkie|**EINVAL —**|
|wszystkie|wszystkie|wszystkie|wszystkie|zero|**EINVAL —**|
|wszystkie|wszystkie|**NULL**|Wystąpił|wszystkie|**EINVAL —**|

## <a name="remarks"></a>Uwagi

**_Lfind_s —** funkcja wykonuje wyszukiwanie liniowe dla wartości *klucza* w tablicy *numer* z elementów *szerokość* bajtów. W odróżnieniu od **bsearch_s —**, **_lfind_s —** nie wymaga tablicy ma zostać posortowana. *Podstawowej* argument jest wskaźnik do podstawy tablicy do wyszukania. *Porównania* argument jest wskaźnik do procedury dostarczone przez użytkownika, która porównuje dwa elementy tablicy, a następnie zwraca wartość określającą ich relacji. **_lfind_s —** wywołania *porównania* rutynowych jeden lub więcej razy podczas wyszukiwania przekazywanie *kontekstu* wskaźnik i wskaźniki do dwóch elementów tablicy przy każdym wywołaniu. *Porównania* procedury należy porównać elementy, a następnie wróć różną od zera (, co oznacza, że elementy różnią się) lub wartość 0 (tzn. elementy są identyczne).

**_lfind_s —** jest podobny do **_lfind —** z wyjątkiem dodawania *kontekstu* wskaźnik do argumentów funkcji porównania i listy parametrów funkcji. *Kontekstu* wskaźnika może być przydatna, jeśli struktura przeszukane danych jest częścią obiektu i *porównania* funkcji ma dostęp do elementów członkowskich obiektu. *Porównania* funkcji można rzutować wskaźnika void do odpowiedniego obiektu członków typu i dostępu do tego obiektu. Dodanie *kontekstu* sprawia, że parametr **_lfind_s —** bardziej bezpieczne, ponieważ dodatkowy kontekst mogą zostać użyte w celu uniknięcia ponownego rozpoczęcia błędów związanych z użyciem zmienne statyczne, aby udostępnić dane *porównania* funkcji.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lfind_s**|\<Search.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
