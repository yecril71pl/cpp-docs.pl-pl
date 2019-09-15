---
title: bsearch
ms.date: 11/04/2016
api_name:
- bsearch
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
- bsearch
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
ms.openlocfilehash: 9e44e85d1c6d73a68da2edd099cdeb6156f9759d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939437"
---
# <a name="bsearch"></a>bsearch

Wykonuje binarne wyszukiwanie posortowanej tablicy. Dostępna jest bezpieczniejsza wersja tej funkcji; Zobacz [bsearch_s](bsearch-s.md).

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
Wskaźnik do podstawy wyszukiwania danych.

*Liczba*<br/>
Liczba elementów.

*width*<br/>
Szerokość elementów.

*porównaniu*<br/>
Funkcja wywołania zwrotnego, która porównuje dwa elementy. Pierwszy jest wskaźnikiem do klucza do wyszukania, a drugi jest wskaźnikiem do elementu tablicy, który będzie porównywany z kluczem.

## <a name="return-value"></a>Wartość zwracana

**bsearch** zwraca wskaźnik do wystąpienia *klucza* w tablicy wskazywanym przez *bazę*. Jeśli nie odnaleziono *klucza* , funkcja zwraca **wartość null**. Jeśli tablica nie znajduje się w kolejności sortowania rosnącej lub zawiera zduplikowane rekordy z identycznymi kluczami, wynik jest nieprzewidywalny.

## <a name="remarks"></a>Uwagi

Funkcja **bsearch** wykonuje binarne wyszukiwanie posortowanej tablicy elementów *liczbowych* , a wszystkie bajty o *szerokości* . Wartość *podstawowa* jest wskaźnikiem do podstawy tablicy, która ma być przeszukiwana, a wartość *klucza* jest poszukiwana. Parametr *Compare* jest wskaźnikiem do procedury dostarczonej przez użytkownika, która porównuje żądany klucz z elementem Array i zwraca jedną z następujących wartości określających ich relację:

|Wartość zwrócona przez procedurę *porównania*|Opis|
|-----------------------------------------|-----------------|
|\< 0|Klucz jest mniejszy niż element tablicy.|
|0|Klucz jest równy elementowi tablicy.|
|> 0|Klucz jest większy niż element tablicy.|

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *Compare*, *Key* lub *Number* ma **wartość null**lub jeśli *Base* ma **wartość null** , a *Liczba* jest różna od zera lub jeśli *Szerokość* wynosi zero, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametrów ](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na `EINVAL` , a funkcja zwraca **wartość null**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**bsearch**|\<STDLIB. h > i \<Search. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program Sortuje tablicę ciągów z qsort, a następnie używa bsearch do znalezienia słowa "Cat".

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
