---
title: bsearch_s
ms.date: 4/2/2020
api_name:
- bsearch_s
- _o_bsearch_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- bsearch_s
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
ms.openlocfilehash: ef8a68f0db45e718af6b17fe0d08c33a6fd61d6c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333845"
---
# <a name="bsearch_s"></a>bsearch_s

Wykonuje wyszukiwanie binarne tablicy posortowane. Ta funkcja jest wersją [bsearch](bsearch.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
void *bsearch_s(
   const void *key,
   const void *base,
   size_t number,
   size_t width,
   int ( __cdecl *compare ) ( void *, const void *key, const void *datum),
   void * context
);
```

### <a name="parameters"></a>Parametry

*Klucz*\
Wskaźnik do klucza do wyszukiwania.

*Podstawowej*\
Wskaźnik do podstawy danych wyszukiwania.

*Numer*\
Liczba elementów.

*Szerokość*\
Szerokość elementów.

*Porównać*\
Wywołanie zwrotne, który porównuje dwa elementy. Pierwszym argumentem jest wskaźnik *kontekstu.* Drugi argument jest wskaźnikiem do *klucza* wyszukiwania. Trzeci argument jest wskaźnikiem do elementu tablicy, który ma być porównywany z *kluczem*.

*Kontekście*\
Wskaźnik do obiektu, do który można uzyskać dostęp w funkcji porównania.

## <a name="return-value"></a>Wartość zwracana

**bsearch_s** zwraca wskaźnik do wystąpienia *klucza* w tablicy wskazywowej według *podstawy*. Jeśli *klucz* nie zostanie znaleziony, funkcja zwraca **wartość NULL**. Jeśli tablica nie jest w kolejności sortowania rosnącego lub zawiera zduplikowane rekordy z identycznymi kluczami, wynik jest nieprzewidywalny.

Jeśli nieprawidłowe parametry są przekazywane do funkcji, wywołuje nieprawidłowy program obsługi parametrów, jak opisano w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **Wartość EINVAL,** a funkcja zwraca **wartość NULL**. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Warunki błędu

|||||||
|-|-|-|-|-|-|
|*key*|*base*|*Porównać*|*numer*|*Szerokość*|**Errno**|
|**Null**|Wszelki|Wszelki|Wszelki|Wszelki|**Einval**|
|Wszelki|**Null**|Wszelki|!= 0|Wszelki|**Einval**|
|Wszelki|Wszelki|Wszelki|Wszelki|= 0|**Einval**|
|Wszelki|Wszelki|**Null**|an|Wszelki|**Einval**|

## <a name="remarks"></a>Uwagi

Funkcja **bsearch_s** wykonuje wyszukiwanie binarne posortowane tablicy elementów *liczbowych,* każdy o rozmiarze *szerokości.* Wartość *podstawowa* jest wskaźnikiem do podstawy tablicy, która ma być przeszukiwana, a *klucz* jest poszukiwaną wartością. Parametr *compare* jest wskaźnikiem do procedury dostarczonej przez użytkownika, która porównuje żądany klucz z elementem tablicy i zwraca jedną z następujących wartości określających ich relację:

|Wartość zwrócona przez *procedurę porównywania*|Opis|
|-----------------------------------------|-----------------|
|\<0|Klucz jest mniejszy niż element tablicy.|
|0|Klucz jest równy element tablicy.|
|> 0|Klucz jest większy niż element tablicy.|

Wskaźnik *kontekstu* może być przydatne, jeśli struktura danych przeszukiwanych jest częścią obiektu, a funkcja porównania musi uzyskać dostęp do elementów członkowskich obiektu. Funkcja *porównywania* może rzutuć wskaźnik void do odpowiedniego typu obiektu i uzyskać dostęp do elementów członkowskich tego obiektu. Dodanie *parametru kontekstu* sprawia, **że bsearch_s** bardziej bezpieczne, ponieważ dodatkowy kontekst może służyć do uniknięcia błędów reentrancy skojarzone z przy użyciu zmiennych statycznych, aby udostępnić dane do funkcji *porównania.*

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**bsearch_s**|\<> i \<search.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program sortuje tablicę ciągów z [qsort_s](qsort-s.md), a następnie używa bsearch_s, aby znaleźć słowo "kot".

```cpp
// crt_bsearch_s.cpp
// This program uses bsearch_s to search a string array,
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
#define ENGLISH_LOCALE "English_US.850"
#endif

#ifdef CODEPAGE_1252
#define ENGLISH_LOCALE "English_US.1252"
#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making it vulnerable to thread conflicts
// (if this were a multithreaded program).

int compare( void *pvlocale, char **str1, char **str2)
{
    char *s1 = *str1;
    char *s2 = *str2;

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(
       s1, s1+strlen(s1),
       s2, s2+strlen(s2) );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};

   char *key = "cat";
   char **result;
   int i;

   /* Sort using Quicksort algorithm: */
   qsort_s( arr,
            sizeof(arr)/sizeof(arr[0]),
            sizeof( char * ),
            (int (*)(void*, const void*, const void*))compare,
            &locale(ENGLISH_LOCALE) );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch_s( &key,
                                arr,
                                sizeof(arr)/sizeof(arr[0]),
                                sizeof( char * ),
                                (int (*)(void*, const void*, const void*))compare,
                                &locale(ENGLISH_LOCALE) );
   if( result )
      printf( "\n%s found at %Fp\n", *result, result );
   else
      printf( "\nCat not found!\n" );
}
```

```Output
cat cow dog goat horse human pig rat
cat found at 002F0F04
```

## <a name="see-also"></a>Zobacz też

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
