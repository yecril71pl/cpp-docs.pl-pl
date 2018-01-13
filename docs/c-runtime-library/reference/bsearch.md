---
title: "bsearch — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: bsearch
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
f1_keywords: bsearch
dev_langs: C++
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1db24ea4be15c4111b94a28323903dd3f2c3ed7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="bsearch"></a>bsearch
Wykonuje wyszukiwanie binarne posortowane tablicy. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [bsearch_s —](../../c-runtime-library/reference/bsearch-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
void *bsearch(   
   const void *key,  
   const void *base,  
   size_t num,  
   size_t width,  
   int ( __cdecl *compare ) (const void *key, const void *datum)   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `key`  
 Obiekt do wyszukania.  
  
 `base`  
 Wskaźnik do podstawowego wyszukiwania danych.  
  
 `num`  
 Liczba elementów.  
  
 `width`  
 Szerokość elementów.  
  
 `compare`  
 Funkcja wywołania zwrotnego, który porównuje dwa elementy. Pierwsza to wskaźnik do klucza wyszukiwania, a drugą jest wartość wskaźnika do elementu tablicy, która ma zostać porównane z kluczem.  
  
## <a name="return-value"></a>Wartość zwracana  
 `bsearch`Zwraca wskaźnik do wystąpienia `key` w tablicy wskazywana przez `base`. Jeśli `key` nie zostanie znaleziony, funkcja zwraca `NULL`. Jeśli tablica nie jest w kolejności rosnącej lub zawiera zduplikowane rekordy z identycznymi kluczami, wynik będzie nieprzewidywalny.  
  
## <a name="remarks"></a>Uwagi  
 `bsearch` Funkcja Wyszukiwanie binarne posortowaną tablicę `num` z elementów `width` rozmiar bajtów. `base` Wartość jest wskaźnik do podstawy tablicy ma zostać wyszukany i `key` jest wartością złożony. `compare` Parametr jest wskaźnikiem do podanego przez użytkownika procedury porównuje żądany klucz do elementu tablicy, która zwraca jedną z następujących wartości, określając ich relacji:  
  
|Wartość zwrócona przez `compare` procedury|Opis|  
|-----------------------------------------|-----------------|  
|\< 0|Klucz jest mniejsza niż elementu tablicy.|  
|0|Klucz jest równa wartości elementu tablicy.|  
|> 0|Klucz jest większy niż element tablicy.|  
  
 Ta funkcja weryfikuje jego parametrów. Jeśli `compare`, `key` lub `num` jest `NULL`, lub jeśli `base` jest `NULL` i *`num` jest różna od zera, lub jeśli `width` wynosi zero, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i funkcja zwraca `NULL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`bsearch`|\<stdlib.h > i \<search.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Ten program sortuje tablicy ciągów z qsort —, a następnie używa bsearch — Aby znaleźć wyraz "kot".  
  
```  
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
 [Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)   
 [_lfind —](../../c-runtime-library/reference/lfind.md)   
 [_lsearch —](../../c-runtime-library/reference/lsearch.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)