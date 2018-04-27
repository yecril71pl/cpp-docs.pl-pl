---
title: qsort — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8d6aea0d0857d26237716464ea4eda778d1e0f85
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="qsort"></a>qsort

Wykonuje szybkie sortowanie. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [qsort_s —](qsort-s.md).

## <a name="syntax"></a>Składnia

```C
void qsort(
   void *base,
   size_t num,
   size_t width,
   int (__cdecl *compare )(const void *, const void *)
);
```

### <a name="parameters"></a>Parametry

*podstawowy* Start tablicy docelowej.

*numer* rozmiar w elementach tablicy.

*szerokość* Element rozmiar w bajtach.

*Porównaj* wskaźnik do procedury dostarczone przez użytkownika, który porównuje dwa elementy tablicy i zwraca wartość określającą ich relacji.

## <a name="remarks"></a>Uwagi

**Qsort —** funkcja implementuje algorytm szybkiego sortowania, aby posortować tablicę *numer* z elementów *szerokość* bajtów. Argument *podstawowej* wskaźnik do podstawy tablicy ma zostać posortowana. **qsort —** zastępuje tej tablicy przy użyciu posortowanych elementów.

**qsort —** wywołania *porównania* rutynowych co najmniej jeden razy podczas sortowania i przekazuje wskaźników do dwóch elementów tablicy przy każdym wywołaniu.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

Procedura porównuje elementy i zwraca jedną z następujących wartości.

|Porównaj wartości zwracanej — funkcja|Opis|
|-----------------------------------|-----------------|
|< 0|**elem1** mniej niż **elem2**|
|0|**elem1** odpowiednikiem **elem2**|
|> 0|**elem1** większa niż **elem2**|

Tablicy jest sortowany w kolejności rosnącej, zgodnie z definicją przez funkcję porównania. Sortowanie tablicy w kolejności malejącej, należy wycofać rozumieniu "większe niż" i "poniżej" w funkcji porównania.

Ta funkcja weryfikuje jego parametrów. Jeśli *porównania* lub *numer* jest **NULL**, lub jeśli *podstawowej* jest **NULL** i **numer* jest różna od zera, lub jeśli *szerokość* jest mniejsza od zera, zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca i **errno** ustawiono **einval —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**qsort**|\<stdlib.h > i \<search.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
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

## <a name="see-also"></a>Zobacz także

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
