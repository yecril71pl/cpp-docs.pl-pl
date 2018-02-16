---
title: "qsort — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- qsort
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- qsort
dev_langs:
- C++
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a39f6edf9dfdf2130bfe9d00cc2a9453f48ad9f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="qsort"></a>qsort
Wykonuje szybkie sortowanie. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [qsort_s —](../../c-runtime-library/reference/qsort-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
void qsort(  
   void *base,  
   size_t num,  
   size_t width,  
   int (__cdecl *compare )(const void *, const void *)   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `base`  
 Początek tablicy docelowej.  
  
 `num`  
 Rozmiar tablicy w elementach.  
  
 `width`  
 Element rozmiar w bajtach.  
  
 `compare`  
 Wskaźnik do procedury dostarczone przez użytkownika, który porównuje dwa elementy tablicy i zwraca wartość określającą ich relacji.  
  
## <a name="remarks"></a>Uwagi  
 `qsort` Funkcja implementuje algorytm szybkiego sortowania, aby posortować tablicę `num` z elementów `width` bajtów. Argument `base` wskaźnik do podstawy tablicy ma zostać posortowana. `qsort` zastąpienie tej tablicy przy użyciu posortowanych elementów.  
  
 `qsort` wywołania `compare` rutynowych co najmniej jeden razy podczas sortowania i przekazuje wskaźników do dwóch elementów tablicy przy każdym wywołaniu.  
  
```  
compare( (void *) & elem1, (void *) & elem2 );  
```  
  
 Procedura porównuje elementy i zwraca jedną z następujących wartości.  
  
|Porównaj wartości zwracanej — funkcja|Opis|  
|-----------------------------------|-----------------|  
|< 0|`elem1` Mniej niż `elem2`|  
|0|`elem1` Wartość równoważna wartości `elem2`|  
|> 0|`elem1` Większa niż `elem2`|  
  
 Tablicy jest sortowany w kolejności rosnącej, zgodnie z definicją przez funkcję porównania. Sortowanie tablicy w kolejności malejącej, należy wycofać rozumieniu "większe niż" i "poniżej" w funkcji porównania.  
  
 Ta funkcja weryfikuje jego parametrów. Jeśli `compare` lub `num` jest `NULL`, lub jeśli `base` jest `NULL` i *`num` jest różna od zera, lub jeśli `width` jest mniejsza od zera, zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca i `errno` ma ustawioną wartość `EINVAL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`qsort`|\<stdlib.h > i \<search.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_qsort.c  
// arguments: every good boy deserves favor  
  
/* This program reads the command-line  
 * parameters and uses qsort to sort them. It  
 * then displays the sorted arguments.  
 */  
  
#include <stdlib.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare( const void *arg1, const void *arg2 );  
  
int main( int argc, char **argv )  
{  
   int i;  
   /* Eliminate argv[0] from sort: */  
   argv++;  
   argc--;  
  
   /* Sort remaining args using Quicksort algorithm: */  
   qsort( (void *)argv, (size_t)argc, sizeof( char * ), compare );  
  
   /* Output sorted list: */  
   for( i = 0; i < argc; ++i )  
      printf( " %s", argv[i] );  
   printf( "\n" );  
}  
  
int compare( const void *arg1, const void *arg2 )  
{  
   /* Compare all of both strings: */  
   return _stricmp( * ( char** ) arg1, * ( char** ) arg2 );  
}  
```  
  
```Output  
boy deserves every favor good  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch —](../../c-runtime-library/reference/bsearch.md)   
 [_lsearch](../../c-runtime-library/reference/lsearch.md)