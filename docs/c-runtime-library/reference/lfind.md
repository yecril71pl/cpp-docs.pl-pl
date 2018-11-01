---
title: _lfind
ms.date: 11/04/2016
apiname:
- _lfind
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
- lfind
- _lfind
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
ms.openlocfilehash: 1508d54d6b2f2566e4aee3afef02af45b28e4f48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579169"
---
# <a name="lfind"></a>_lfind

Wykonuje wyszukiwanie liniowe dla określonego klucza. Bardziej bezpieczna wersja ta funkcja jest dostępna; zobacz [_lfind_s —](lfind-s.md).

## <a name="syntax"></a>Składnia

```C
void *_lfind(
   const void *key,
   const void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Obiekt do wyszukania.

*base*<br/>
Wskaźnik do bazy danych wyszukiwania.

*Numer*<br/>
Liczba elementów tablicy.

*width*<br/>
Szerokość elementów tablicy.

*Porównanie*<br/>
Wskaźnik do procedury porównania. Pierwszy parametr jest wskaźnikiem do klucza dla wyszukiwania. Drugi parametr jest wskaźnik do elementu tablicy, który można porównać z kluczem.

## <a name="return-value"></a>Wartość zwracana

Jeśli klucz zostanie znaleziony, **_lfind —** zwraca wskaźnik do elementu tablicy, od *podstawowy* odpowiadający *klucz*. Jeśli klucz nie zostanie znaleziony, **_lfind —** zwraca **NULL**.

## <a name="remarks"></a>Uwagi

**_Lfind —** funkcja wykonuje wyszukiwanie liniowe dla wartości *klucz* tablicę *numer* elementów, z których każdy z *szerokość* bajtów. W odróżnieniu od **bsearch —**, **_lfind —** nie wymaga tablicy, która ma zostać posortowana. *Podstawowy* argument jest wskaźnikiem do podstawy tablicy, który ma być przeszukiwany. *Porównania* argument jest wskaźnikiem do procedury dostarczone przez użytkownika, która porównuje dwa elementy tablicy, a następnie zwraca wartość określającą, ich relacje. **_lfind —** wywołania *porównania* rutynowych jeden lub więcej razy podczas wyszukiwania, przekazując wskaźniki do dwóch elementów tablicy przy każdym wywołaniu. *Porównania* procedury musi porównywania elementów, a następnie zwracają wartość różną od zera (tzn. elementy są różnych) lub od 0 (co oznacza, że elementy są identyczne).

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *porównania*, *klucz* lub *numer* jest **NULL**, lub jeśli *podstawowy* jest **NULL**i *numer* jest różna od zera, lub jeśli *szerokość* jest mniejsza niż zero, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca **NULL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lfind**|\<Search.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_lfind.c
// This program uses _lfind to search a string array
// for an occurrence of "hello".

#include <search.h>
#include <string.h>
#include <stdio.h>

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}

int main( )
{
   char *arr[] = {"Hi", "Hello", "Bye"};
   int n = sizeof(arr) / sizeof(char*);
   char **result;
   char *key = "hello";

   result = (char **)_lfind( &key, arr,
                      &n, sizeof(char *), compare );

   if( result )
      printf( "%s found\n", *result );
   else
      printf( "hello not found!\n" );
}
```

```Output
Hello found
```

## <a name="see-also"></a>Zobacz także

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
