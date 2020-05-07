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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 3d9c3481b37e94dbb59ee7356caafc53501045ea
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913254"
---
# <a name="qsort"></a>qsort

Wykonuje szybkie sortowanie. Dostępna jest bezpieczniejsza wersja tej funkcji; Zobacz [qsort_s](qsort-s.md).

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

*Liczba*<br/>
Rozmiar tablicy w elementach.

*Szerokość*<br/>
Rozmiar elementu w bajtach.

*porównaniu*<br/>
Wskaźnik do procedury dostarczonej przez użytkownika, która porównuje dwa elementy tablicy i zwraca wartość określającą ich relację.

## <a name="remarks"></a>Uwagi

Funkcja **qsort** implementuje algorytm szybkiego sortowania, aby posortować tablicę elementów *liczbowych* , a każda z nich ma *Szerokość* . *Podstawa* argumentu jest wskaźnikiem do podstawy tablicy, która ma zostać posortowana. **qsort** zastępuje tę tablicę przy użyciu posortowanych elementów.

**qsort** wywołuje procedurę *porównania* w jeden lub więcej razy podczas sortowania i przekazuje wskaźniki do dwóch elementów tablicy dla każdego wywołania.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

Procedura porównuje elementy i zwraca jedną z następujących wartości.

|Porównywanie zwracanej wartości funkcji|Opis|
|-----------------------------------|-----------------|
|< 0|**elem1** mniejsze niż **elem2**|
|0|**elem1** równoważne **elem2**|
|> 0|**elem1** większe niż **elem2**|

Tablica jest sortowana w kolejności rosnącej, zgodnie z definicją w funkcji porównania. Aby posortować tablicę w kolejności malejącej, Odwróć wartość "większe niż" i "mniejsze niż" w funkcji porównywania.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *Compare* lub *Number* ma **wartość null**lub jeśli *podstawa* ma **wartość null** , a *Liczba* jest różna od zera, lub jeśli *Szerokość* jest mniejsza od zera, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca i **errno** jest ustawiona na **EINVAL**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**qsort**|\<STDLIB. h> i \<Search. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
