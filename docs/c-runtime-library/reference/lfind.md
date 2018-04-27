---
title: _lfind — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 488863a32319fac17f5d1c84f56edaeeb63ff0ce
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="lfind"></a>_lfind

Wykonuje wyszukiwanie liniowe dla określonego klucza. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [_lfind_s —](lfind-s.md).

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

*Porównaj*<br/>
Wskaźnik do porównania procedury. Pierwszym parametrem jest wskaźnik do klucza dla wyszukiwania. Drugi parametr jest wskaźnik do elementu tablicy ma zostać porównane z kluczem.

## <a name="return-value"></a>Wartość zwracana

Jeśli klucz zostanie znaleziony, **_lfind —** zwraca wskaźnik do elementu tablicy w *podstawowej* odpowiadającego *klucza*. Jeśli klucz nie zostanie znaleziony, **_lfind —** zwraca **NULL**.

## <a name="remarks"></a>Uwagi

**_Lfind —** funkcja wykonuje wyszukiwanie liniowe dla wartości *klucza* w tablicy *numer* z elementów *szerokość* bajtów. W odróżnieniu od **bsearch —**, **_lfind —** nie wymaga tablicy ma zostać posortowana. *Podstawowej* argument jest wskaźnik do podstawy tablicy do wyszukania. *Porównania* argument jest wskaźnik do procedury dostarczone przez użytkownika, która porównuje dwa elementy tablicy, a następnie zwraca wartość określającą ich relacji. **_lfind —** wywołania *porównania* rutynowych jeden lub więcej razy podczas wyszukiwania przekazywanie wskaźników do dwóch elementów tablicy przy każdym wywołaniu. *Porównania* procedury należy porównać elementy, a następnie wróć różną od zera (to znaczy elementy są różne) lub wartość 0 (tzn. elementy są identyczne).

Ta funkcja weryfikuje jego parametrów. Jeśli *porównania*, *klucza* lub *numer* jest **NULL**, lub jeśli *podstawowej* ma wartość NULL i **numer*  jest różna od zera, lub jeśli *szerokość* jest mniejsza od zera, zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i funkcja zwraca **NULL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lfind**|\<Search.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
