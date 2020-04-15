---
title: bsearch
ms.date: 4/2/2020
api_name:
- bsearch
- _o_bsearch
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
- bsearch
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
ms.openlocfilehash: efad391eb2512cfa59cc3597430a84727676f27e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333804"
---
# <a name="bsearch"></a>bsearch

Wykonuje wyszukiwanie binarne tablicy posortowane. Dostępna jest bezpieczniejsza wersja tej funkcji; patrz [bsearch_s](bsearch-s.md).

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

*Klucz*\
Wskaźnik do klucza do wyszukiwania.

*Podstawowej*\
Wskaźnik do podstawy danych wyszukiwania.

*Numer*\
Liczba elementów.

*Szerokość*\
Szerokość elementów.

*Porównać*\
Wywołanie zwrotne, który porównuje dwa elementy. Pierwszy to wskaźnik do klucza wyszukiwania, a drugi jest wskaźnikiem do elementu tablicy, który ma zostać porównany z kluczem.

## <a name="return-value"></a>Wartość zwracana

**bsearch** zwraca wskaźnik do wystąpienia *klucza* w tablicy wskazywania według *podstawy*. Jeśli *klucz* nie zostanie znaleziony, funkcja zwraca **wartość NULL**. Jeśli tablica nie jest w kolejności sortowania rosnącego lub zawiera zduplikowane rekordy z identycznymi kluczami, wynik jest nieprzewidywalny.

## <a name="remarks"></a>Uwagi

Funkcja **bsearch** wykonuje wyszukiwanie binarne posortowane tablicy elementów *liczbowych,* każdy o rozmiarze *szerokości.* Wartość *podstawowa* jest wskaźnikiem do podstawy tablicy, która ma być przeszukiwana, a *klucz* jest poszukiwaną wartością. Parametr *compare* jest wskaźnikiem do procedury dostarczonej przez użytkownika, która porównuje żądany klucz z elementem tablicy. Zwraca jedną z następujących wartości, które określają ich relacji:

|Wartość zwrócona przez *procedurę porównywania*|Opis|
|-----------------------------------------|-----------------|
|\<0|Klucz jest mniejszy niż element tablicy.|
|0|Klucz jest równy element tablicy.|
|> 0|Klucz jest większy niż element tablicy.|

Ta funkcja sprawdza poprawność jego parametrów. Jeśli *porównaj*, *klucz* lub *liczba* ma **wartość NULL**lub jeśli *podstawa* ma **wartość NULL,** a *liczba* jest niezerowa, lub jeśli *szerokość* wynosi zero, funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w obszarze Sprawdzanie [poprawności parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, **errno** jest `EINVAL` ustawiona na i funkcja zwraca **NULL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**bsearch**|\<> i \<search.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program sortuje tablicę ciągów z qsort, a następnie używa bsearch, aby znaleźć słowo "kot".

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

## <a name="see-also"></a>Zobacz też

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
