---
title: "bsearch_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- bsearch_s
dev_langs:
- C++
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5c1ec2b76d64f9a65d19362f592483490c8b9bb3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="bsearchs"></a>bsearch_s
Wykonuje wyszukiwanie binarne posortowane tablicy. To jest wersja [bsearch —](../../c-runtime-library/reference/bsearch.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
void *bsearch_s(   
   const void *key,  
   const void *base,  
   size_t num,  
   size_t width,  
   int ( __cdecl *compare ) ( void *, const void *key, const void *datum),  
   void * context  
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
 Funkcja wywołania zwrotnego, który porównuje dwa elementy. Pierwszy argument jest `context` wskaźnika. Drugi argument jest wskaźnikiem do `key` wyszukiwania. Trzeci argument jest wskaźnik do elementu tablicy, która ma zostać porównane z `key`.  
  
 `context`  
 Wskaźnik do obiektu, który jest dostępny w funkcji porównania.  
  
## <a name="return-value"></a>Wartość zwracana  
 `bsearch_s` Zwraca wskaźnik do wystąpienia `key` w tablicy wskazywana przez `base`. Jeśli `key` nie zostanie znaleziony, funkcja zwraca `NULL`. Jeśli tablica nie jest w kolejności rosnącej lub zawiera zduplikowane rekordy z identycznymi kluczami, wynik będzie nieprzewidywalny.  
  
 Jeśli nieprawidłowe parametry są przekazywane do funkcji, zgodnie z opisem w wywołaniu program obsługi nieprawidłowych parametrów [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i funkcja zwraca `NULL`. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|||||||  
|-|-|-|-|-|-|  
|`key`|`base`|`compare`|`num`|`width`|`errno`|  
|`NULL`|wszystkie|wszystkie|wszystkie|wszystkie|`EINVAL`|  
|wszystkie|`NULL`|wszystkie|!= 0|wszystkie|`EINVAL`|  
|wszystkie|wszystkie|wszystkie|wszystkie|= 0|`EINVAL`|  
|wszystkie|wszystkie|`NULL`|an|wszystkie|`EINVAL`|  
  
## <a name="remarks"></a>Uwagi  
 `bsearch_s` Funkcja Wyszukiwanie binarne posortowaną tablicę `num` z elementów `width` rozmiar bajtów. `base` Wartość jest wskaźnik do podstawy tablicy ma zostać wyszukany i `key` jest wartością złożony. `compare` Parametr jest wskaźnikiem do podanego przez użytkownika procedury porównuje żądany klucz do elementu tablicy, która zwraca jedną z następujących wartości, określając ich relacji:  
  
|Wartość zwrócona przez `compare` procedury|Opis|  
|-----------------------------------------|-----------------|  
|\< 0|Klucz jest mniejsza niż elementu tablicy.|  
|0|Klucz jest równa wartości elementu tablicy.|  
|> 0|Klucz jest większy niż element tablicy.|  
  
 `context` Wskaźnika mogą być użyteczne, jeśli struktura przeszukane danych wchodzi w skład obiektu, a funkcja porównywania ma dostęp do elementów członkowskich obiektu. `compare` Funkcja może oddać void wskaźnika do odpowiedniego obiektu członków typu i dostępu do tego obiektu. Dodanie `context` sprawia, że parametr `bsearch_s` bardziej bezpieczne, ponieważ dodatkowy kontekst pozwala uniknąć związanych z użyciem zmienne statyczne, aby udostępnić dane usterki wielobieżność `compare` funkcji.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`bsearch_s`|\<stdlib.h > i \<search.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Ten program sortuje tablicy ciągów z [qsort_s —](../../c-runtime-library/reference/qsort-s.md), a następnie używa bsearch_s — Aby znaleźć wyraz "kot".  
  
```  
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
 [Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)   
 [_lfind —](../../c-runtime-library/reference/lfind.md)   
 [_lsearch —](../../c-runtime-library/reference/lsearch.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)