---
title: bsearch_s
ms.date: 11/04/2016
api_name:
- bsearch_s
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
ms.openlocfilehash: 9bcd18add216bb0fc2f203183d82e37ede65dba5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943484"
---
# <a name="bsearch_s"></a>bsearch_s

Wykonuje binarne wyszukiwanie posortowanej tablicy. Jest to wersja programu [bsearch](bsearch.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Klucz*<br/>
Obiekt do wyszukania.

*base*<br/>
Wskaźnik do podstawy wyszukiwania danych.

*Liczba*<br/>
Liczba elementów.

*width*<br/>
Szerokość elementów.

*porównaniu*<br/>
Funkcja wywołania zwrotnego, która porównuje dwa elementy. Pierwszy argument jest wskaźnikiem *kontekstu* . Drugi argument jest wskaźnikiem do *klucza* do wyszukania. Trzeci argument jest wskaźnikiem do elementu tablicy, który będzie porównywany z *kluczem*.

*Context*<br/>
Wskaźnik do obiektu, do którego można uzyskać dostęp w funkcji porównania.

## <a name="return-value"></a>Wartość zwracana

**bsearch_s** zwraca wskaźnik do wystąpienia *klucza* w tablicy wskazywanym przez *bazę*. Jeśli nie odnaleziono *klucza* , funkcja zwraca **wartość null**. Jeśli tablica nie znajduje się w kolejności sortowania rosnącej lub zawiera zduplikowane rekordy z identycznymi kluczami, wynik jest nieprzewidywalny.

Jeśli do funkcji są przenoszone nieprawidłowe parametry, procedura obsługi nieprawidłowego parametru jest wywoływana, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca **wartość null**. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Warunki błędów

|||||||
|-|-|-|-|-|-|
|*Klucz*|*base*|*porównaniu*|*Liczba*|*width*|**errno**|
|**NULL**|Ile|Ile|Ile|Ile|**EINVAL**|
|Ile|**NULL**|Ile|!= 0|Ile|**EINVAL**|
|Ile|Ile|Ile|Ile|= 0|**EINVAL**|
|Ile|Ile|**NULL**|Wskazani|Ile|**EINVAL**|

## <a name="remarks"></a>Uwagi

Funkcja **bsearch_s** wykonuje binarne wyszukiwanie posortowanej tablicy elementów *liczbowych* , a wszystkie bajty o *szerokości* . Wartość *podstawowa* jest wskaźnikiem do podstawy tablicy, która ma być przeszukiwana, a wartość *klucza* jest poszukiwana. Parametr *Compare* jest wskaźnikiem do procedury dostarczonej przez użytkownika, która porównuje żądany klucz z elementem Array i zwraca jedną z następujących wartości określających ich relację:

|Wartość zwrócona przez procedurę *porównania*|Opis|
|-----------------------------------------|-----------------|
|\< 0|Klucz jest mniejszy niż element tablicy.|
|0|Klucz jest równy elementowi tablicy.|
|> 0|Klucz jest większy niż element tablicy.|

Wskaźnik *kontekstu* może być przydatny, jeśli przeszukiwana struktura danych jest częścią obiektu, a funkcja porównywania musi uzyskać dostęp do elementów członkowskich obiektu. Funkcja *Compare* może rzutować wskaźnik void na odpowiedni typ obiektu i uzyskać dostęp do elementów członkowskich tego obiektu. Dodanie parametru *Context* sprawia, że **bsearch_s** bezpieczniejszy, ponieważ można użyć dodatkowego kontekstu, aby uniknąć błędów współużytkowania wątkowości skojarzonych z użyciem zmiennych statycznych w celu udostępnienia danych funkcji *Compare* .

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**bsearch_s**|\<STDLIB. h > i \<Search. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program Sortuje tablicę ciągów z [qsort_s](qsort-s.md), a następnie używa bsearch_s do znalezienia słowa "Cat".

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

## <a name="see-also"></a>Zobacz także

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
