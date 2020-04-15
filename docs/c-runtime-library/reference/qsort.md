---
title: qsort
ms.date: 4/2/2020
api_name:
- qsort
- _o_qsort
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- qsort
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
ms.openlocfilehash: 09de57e206eb6fd4a75a0a9444332136aeee0e9d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338248"
---
# <a name="qsort"></a>qsort

Wykonuje szybkie sortowanie. Dostępna jest bezpieczniejsza wersja tej funkcji; patrz [qsort_s](qsort-s.md).

## <a name="syntax"></a>Składnia

```C
void qsort(
   void *base,
   size_t number,
   size_t width,
   int (__cdecl *compare )(const void *, const void *)
);
```

### <a name="parameters"></a>Parametry

*base*<br/>
Początek tablicy docelowej.

*numer*<br/>
Rozmiar tablicy w elementach.

*Szerokość*<br/>
Rozmiar elementu w bajtach.

*Porównać*<br/>
Wskaźnik do procedury dostarczonej przez użytkownika, która porównuje dwa elementy tablicy i zwraca wartość, która określa ich relację.

## <a name="remarks"></a>Uwagi

Funkcja **qsort** implementuje algorytm szybkiego sortowania do sortowania tablicy elementów *liczbowych,* każdy z bajtów *szerokości.* *Podstawa* argumentu jest wskaźnikiem do podstawy tablicy, która ma zostać posortowana. **qsort** zastępuje tę tablicę przy użyciu posortowanych elementów.

**qsort** wywołuje *rutynowe porównanie* jeden lub więcej razy podczas sortowania i przekazuje wskaźniki do dwóch elementów tablicy w każdym wywołaniu.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

Procedura porównuje elementy i zwraca jedną z następujących wartości.

|Porównaj wartość zwracaną funkcji|Opis|
|-----------------------------------|-----------------|
|< 0|**elem1** mniej niż **elem2**|
|0|**elem1** odpowiednik **elem2**|
|> 0|**elem1** większy niż **elem2**|

Tablica jest sortowana w kolejności zwiększania, zgodnie z definicją funkcji porównania. Aby posortować tablicę w kolejności malejącej, należy odwrócić poczucie "większe niż" i "mniej niż" w funkcji porównania.

Ta funkcja sprawdza poprawność jego parametrów. Jeśli *porównanie* lub *liczba* ma **wartość NULL**lub jeśli *podstawa* ma **wartość NULL,** a *liczba* jest niezerowa, lub jeśli *szerokość* jest mniejsza niż zero, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w obszarze Sprawdzanie [poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcja zwraca, a **errno** jest ustawiona na **EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**qsort**|\<> i \<search.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
