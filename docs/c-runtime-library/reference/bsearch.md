---
title: bsearch — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bsearch
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
- bsearch
dev_langs:
- C++
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 85f9dc8bcaf44ade966ec76a57e34c5c06c4935e
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="bsearch"></a>bsearch

Wykonuje wyszukiwanie binarne posortowane tablicy. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [bsearch_s —](bsearch-s.md).

## <a name="syntax"></a>Składnia

```C
void *bsearch(
   const void *key,
   const void *base,
   size_t num,
   size_t width,
   int ( __cdecl *compare ) (const void *key, const void *datum)
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

*Porównaj*<br/>
Funkcja wywołania zwrotnego, który porównuje dwa elementy. Pierwsza to wskaźnik do klucza wyszukiwania, a drugą jest wartość wskaźnika do elementu tablicy, która ma zostać porównane z kluczem.

## <a name="return-value"></a>Wartość zwracana

**bsearch —** zwraca wskaźnik do wystąpienia *klucza* w tablicy wskazywana przez *podstawowej*. Jeśli *klucza* nie zostanie znaleziony, funkcja zwraca **NULL**. Jeśli tablica nie jest w kolejności rosnącej lub zawiera zduplikowane rekordy z identycznymi kluczami, wynik będzie nieprzewidywalny.

## <a name="remarks"></a>Uwagi

**Bsearch —** funkcja Wyszukiwanie binarne posortowaną tablicę *numer* z elementów *szerokość* rozmiar bajtów. *Podstawowej* wartość jest wskaźnik do podstawy tablicy ma zostać wyszukany i *klucza* jest wartością złożony. *Porównania* parametr jest wskaźnikiem do podanego przez użytkownika procedury porównuje żądany klucz do elementu tablicy, która zwraca jedną z następujących wartości, określając ich relacji:

|Wartość zwrócona przez *porównania* procedury|Opis|
|-----------------------------------------|-----------------|
|\< 0|Klucz jest mniejsza niż elementu tablicy.|
|0|Klucz jest równa wartości elementu tablicy.|
|> 0|Klucz jest większy niż element tablicy.|

Ta funkcja weryfikuje jego parametrów. Jeśli *porównania*, *klucza* lub *numer* jest **NULL**, lub jeśli *podstawowej* jest **NULL**i **numer* jest różna od zera, lub jeśli *szerokość* wynosi zero, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i funkcja zwraca **NULL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**bsearch**|\<stdlib.h > i \<search.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program sortuje tablicy ciągów z qsort —, a następnie używa bsearch — Aby znaleźć wyraz "kot".

```C
// crt_bsearch.c
#include <search.h>
#include <string.h>
#include <stdio.h>

int compare( char **arg1, char **arg2 )
{
   /* Compare all of both strings: */
   return _strcmpi( *arg1, *arg2 );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};
   char **result;
   char *key = "cat";
   int i;

   /* Sort using Quicksort algorithm: */
   qsort( (void *)arr, sizeof(arr)/sizeof(arr[0]), sizeof( char * ), (int (*)(const
   void*, const void*))compare );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch( (char *) &key, (char *)arr, sizeof(arr)/sizeof(arr[0]),
                              sizeof( char * ), (int (*)(const void*, const void*))compare );
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
