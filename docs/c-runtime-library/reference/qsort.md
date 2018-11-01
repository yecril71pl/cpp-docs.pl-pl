---
title: qsort
ms.date: 11/04/2016
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
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
ms.openlocfilehash: e912a7a53619e9347cf2c0cd40adf0f9162b314b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618494"
---
# <a name="qsort"></a>qsort

Wykonuje szybkie sortowanie. Bardziej bezpieczna wersja ta funkcja jest dostępna; zobacz [qsort_s —](qsort-s.md).

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

<br/>
Początek tablicy docelowej.

*Numer*<br/>
Rozmiar tablicy w elementach.

*width*<br/>
Element rozmiar w bajtach.

*Porównanie*<br/>
Wskaźnik do procedury dostarczone przez użytkownika, która porównuje dwa elementy tablicy i zwraca wartość, która określa ich relacje.

## <a name="remarks"></a>Uwagi

**Qsort —** funkcja implementuje algorytm szybkiego sortowania, aby posortować tablicę *numer* elementów, z których każdy z *szerokość* bajtów. Argument *podstawowy* jest wskaźnikiem do podstawy tablicy, która ma zostać posortowana. **qsort —** zastępuje tej tablicy przy użyciu posortowanych elementów.

**qsort —** wywołania *porównania* rutynowych jeden lub więcej razy w ciągu sortowanie i przekazuje wskaźniki do dwóch elementów tablicy przy każdym wywołaniu.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

Procedura porównuje elementy i zwraca jedną z następujących wartości.

|Porównaj wartości zwracanej funkcji|Opis|
|-----------------------------------|-----------------|
|< 0|**elem1** mniej niż **elem2**|
|0|**elem1** odpowiednikiem **elem2**|
|> 0|**elem1** większa **elem2**|

Tablica jest sortowane rosnąco, zgodnie z definicją funkcji porównywania. Aby posortować tablicę w kolejności malejącej, odwrócić sens "równy" i "poniżej" w funkcji porównywania.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *porównania* lub *numer* jest **o wartości NULL**, lub jeśli *podstawowy* jest **NULL** i **numer* jest różna od zera, lub jeśli *szerokość* jest mniejsza niż zero, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca i **errno** ustawiono **EINVAL**.

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
