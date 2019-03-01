---
title: bsearch
ms.date: 11/04/2016
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- bsearch
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
ms.openlocfilehash: e170ce67d22c0d97825a7eb754546a29daac6d89
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210461"
---
# <a name="bsearch"></a>bsearch

Wykonuje wyszukiwanie binarne posortowany tablicy. Bardziej bezpieczna wersja ta funkcja jest dostępna; zobacz [bsearch_s —](bsearch-s.md).

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

*compare*<br/>
Funkcja wywołania zwrotnego, która porównuje dwa elementy. Pierwszy jest wskaźnikiem do klucza wyszukiwania, a drugą jest wartość wskaźnika do elementu tablicy, który można porównać z kluczem.

## <a name="return-value"></a>Wartość zwracana

**bsearch —** zwraca wskaźnik do wystąpienia *klucz* w tablicy, do których prowadzą *podstawowy*. Jeśli *klucz* nie zostanie znaleziony, funkcja zwraca **NULL**. Jeśli tablica nie znajduje się w kolejności rosnącej lub zawiera zduplikowane rekordy z identycznymi kluczami, wynik jest nieprzewidywalne.

## <a name="remarks"></a>Uwagi

**Bsearch —** — funkcja Wyszukiwanie binarne posortowaną tablicę *numer* elementów, z których każdy z *szerokość* bajtów. *Podstawowy* wartość jest wskaźnikiem do podstawy tablicy, które mają być wyszukiwane i *klucza* jest wartością niestabilna. *Porównania* parametr jest wskaźnikiem do procedury dostarczone przez użytkownika, który porównuje żądany klucz do elementu tablicy i zwraca jedną z następujących wartości, określając ich relacji:

|Wartość zwrócona przez obiekt *porównania* procedury|Opis|
|-----------------------------------------|-----------------|
|\< 0|Klucz jest mniejsza niż elementu tablicy.|
|0|Klucz jest równa elementu tablicy.|
|> 0|Klucz jest większy niż element tablicy.|

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *porównania*, *klucz* lub *numer* jest **NULL**, lub jeśli *podstawowy* jest **NULL**i *numer* jest różna od zera, lub jeśli *szerokość* wynosi zero, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono `EINVAL` a funkcja zwraca **NULL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**bsearch**|\<stdlib.h > i \<search.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program sortuje tablicy ciągów przy użyciu qsort —, a następnie używa bsearch — można znaleźć słowo "cat".

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
