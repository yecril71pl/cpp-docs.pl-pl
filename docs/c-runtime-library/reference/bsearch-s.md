---
title: bsearch_s
ms.date: 11/04/2016
apiname:
- bsearch_s
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- bsearch_s
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
ms.openlocfilehash: 56c5fa45a9d8f9ac9b22474601934d3994da55e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349254"
---
# <a name="bsearchs"></a>bsearch_s

Wykonuje wyszukiwanie binarne posortowany tablicy. To jest wersja [bsearch —](bsearch.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Wskaźnik do podstawowego wyszukiwania danych.

*Numer*<br/>
Liczba elementów.

*width*<br/>
Szerokość elementów.

*compare*<br/>
Funkcja wywołania zwrotnego, która porównuje dwa elementy. Pierwszy argument jest *kontekstu* wskaźnika. Drugi argument jest wskaźnikiem do *klucz* wyszukiwania. Trzeci argument jest wskaźnikiem do elementu tablicy, która ma zostać porównane z *klucz*.

*Kontekst*<br/>
Wskaźnik do obiektu, który może być dostępne w funkcji porównywania.

## <a name="return-value"></a>Wartość zwracana

**bsearch_s —** zwraca wskaźnik do wystąpienia *klucz* w tablicy, do których prowadzą *podstawowy*. Jeśli *klucz* nie zostanie znaleziony, funkcja zwraca **NULL**. Jeśli tablica nie znajduje się w kolejności rosnącej lub zawiera zduplikowane rekordy z identycznymi kluczami, wynik jest nieprzewidywalne.

Jeśli nieprawidłowe parametry są przekazywane do funkcji, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca **NULL**. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Warunki błędów

|||||||
|-|-|-|-|-|-|
|*Klucz*|*base*|*compare*|*Numer*|*width*|**numer błędu**|
|**NULL**|Wszystkie|Wszystkie|Wszystkie|Wszystkie|**EINVAL**|
|Wszystkie|**NULL**|Wszystkie|!= 0|Wszystkie|**EINVAL**|
|Wszystkie|Wszystkie|Wszystkie|Wszystkie|= 0|**EINVAL**|
|Wszystkie|Wszystkie|**NULL**|Usługi|Wszystkie|**EINVAL**|

## <a name="remarks"></a>Uwagi

**Bsearch_s —** — funkcja Wyszukiwanie binarne posortowaną tablicę *numer* elementów, z których każdy z *szerokość* bajtów. *Podstawowy* wartość jest wskaźnikiem do podstawy tablicy, które mają być wyszukiwane i *klucza* jest wartością niestabilna. *Porównania* parametr jest wskaźnikiem do procedury dostarczone przez użytkownika, który porównuje żądany klucz do elementu tablicy i zwraca jedną z następujących wartości, określając ich relacji:

|Wartość zwrócona przez obiekt *porównania* procedury|Opis|
|-----------------------------------------|-----------------|
|\< 0|Klucz jest mniejsza niż elementu tablicy.|
|0|Klucz jest równa elementu tablicy.|
|> 0|Klucz jest większy niż element tablicy.|

*Kontekstu* wskaźnik może być przydatne, jeśli struktura wyszukiwanych danych jest częścią obiektu, a funkcja porównania dostęp do elementów członkowskich obiektu. *Porównania* funkcji może rzutować wskaźnika void do odpowiedniego obiektu typu i dostęp do elementów członkowskich tego obiektu. Dodanie *kontekstu* sprawia, że parametr **bsearch_s —** bezpieczniejsze, ponieważ dodatkowy kontekst pozwala uniknąć błędów współużytkowania wątkowości, związanych z użyciem statyczne zmienne, aby udostępnić dane *porównania* funkcji.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**bsearch_s**|\<stdlib.h > i \<search.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program sortuje tablicy ciągów przy użyciu [qsort_s —](qsort-s.md), a następnie używa bsearch_s — można znaleźć słowo "cat".

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
