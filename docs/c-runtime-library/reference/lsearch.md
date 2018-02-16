---
title: "_lsearch — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _lsearch
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
- _lsearch
- lsearch
dev_langs:
- C++
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eb4cb64b9287de11a894a8ca7c7cdd4490fcc446
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="lsearch"></a>_lsearch
Wykonuje wyszukiwanie liniowe dla wartości; dodaje do końca listy, jeśli nie można odnaleźć. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [_lsearch_s —](../../c-runtime-library/reference/lsearch-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
void *_lsearch(  
   const void *key,  
   void *base,  
   unsigned int *num,  
   unsigned int width,  
   int (__cdecl *compare)(const void *, const void *)   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `key`  
 Obiekt do wyszukania.  
  
 `base`  
 Wskaźnik do podstawy tablicy do wyszukania.  
  
 `num`  
 Liczba elementów.  
  
 `width`  
 Szerokość każdego elementu tablicy.  
  
 `compare`  
 Wskaźnik do procedury porównania. Pierwszym parametrem jest wskaźnik do klucza dla wyszukiwania. Drugi parametr jest wskaźnik do elementu tablicy ma zostać porównane z kluczem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli klucz zostanie znaleziony, `_lsearch` zwraca wskaźnik do elementu tablicy w `base` , które odpowiadają `key`. Jeśli klucz nie zostanie znaleziony, `_lsearch` zwraca wskaźnik do nowo dodany element na końcu tablicy.  
  
## <a name="remarks"></a>Uwagi  
 `_lsearch` Funkcja wykonuje wyszukiwanie liniowe dla wartości `key` w tablicy `num` z elementów `width` bajtów. W odróżnieniu od `bsearch`, `_lsearch` nie wymaga tablicy ma zostać posortowana. Jeśli `key` nie zostanie znaleziony, `_lsearch` dodaje go do końca tablicy i zwiększa `num`.  
  
 `compare` Argument jest wskaźnik do procedury dostarczone przez użytkownika, który porównuje dwa elementy tablicy i zwraca wartość określającą ich relacji. `_lsearch` wywołania `compare` rutynowych jeden lub więcej razy podczas wyszukiwania przekazywanie wskaźników do dwóch elementów tablicy przy każdym wywołaniu. `compare` należy porównać elementy i zwracać różną od zera (to znaczy elementy są inne) lub wartość 0 (tzn. elementy są identyczne).  
  
 Ta funkcja weryfikuje jego parametrów. Jeśli `compare`, `key` lub `num` jest `NULL`, lub jeśli `base` ma wartość NULL i *`num` jest różna od zera, lub jeśli `width` jest mniejsza od zera, zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [ Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i funkcja zwraca `NULL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_lsearch`|\<search.h>|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_lsearch.c  
#include <search.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare( const void *arg1, const void *arg2 );  
  
int main(void)  
{  
   char * wordlist[4] = { "hello", "thanks", "bye" };  
                            // leave room to grow...  
   int n = 3;  
   char **result;  
   char *key = "extra";  
   int i;  
  
   printf( "wordlist before _lsearch:" );  
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );  
   printf( "\n" );  
  
   result = (char **)_lsearch( &key, wordlist,   
                      &n, sizeof(char *), compare );  
  
   printf( "wordlist after _lsearch:" );  
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );  
   printf( "\n" );  
}  
  
int compare(const void *arg1, const void *arg2 )  
{  
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );  
}  
```  
  
```Output  
wordlist before _lsearch: hello thanks bye  
wordlist after _lsearch: hello thanks bye extra  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch —](../../c-runtime-library/reference/bsearch.md)   
 [_lfind —](../../c-runtime-library/reference/lfind.md)   
 [_lsearch_s](../../c-runtime-library/reference/lsearch-s.md)