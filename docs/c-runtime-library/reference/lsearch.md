---
title: _lsearch — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2aaf6626b2f7005181640f77026b6924c39cd325
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="lsearch"></a>_lsearch

Wykonuje wyszukiwanie liniowe dla wartości; dodaje do końca listy, jeśli nie można odnaleźć. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [_lsearch_s —](lsearch-s.md).

## <a name="syntax"></a>Składnia

```C
void *_lsearch(
   const void *key,
   void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Obiekt do wyszukania.

*base*<br/>
Wskaźnik do podstawy tablicy do wyszukania.

*Numer*<br/>
Liczba elementów.

*width*<br/>
Szerokość każdego elementu tablicy.

*Porównaj*<br/>
Wskaźnik do procedury porównania. Pierwszym parametrem jest wskaźnik do klucza dla wyszukiwania. Drugi parametr jest wskaźnik do elementu tablicy ma zostać porównane z kluczem.

## <a name="return-value"></a>Wartość zwracana

Jeśli klucz zostanie znaleziony, **_lsearch —** zwraca wskaźnik do elementu tablicy w *podstawowej* odpowiadającego *klucza*. Jeśli klucz nie zostanie znaleziony, **_lsearch —** zwraca wskaźnik do nowo dodany element na końcu tablicy.

## <a name="remarks"></a>Uwagi

**_Lsearch —** funkcja wykonuje wyszukiwanie liniowe dla wartości *klucza* w tablicy *numer* z elementów *szerokość* bajtów. W odróżnieniu od **bsearch —**, **_lsearch —** nie wymaga tablicy ma zostać posortowana. Jeśli *klucza* nie zostanie znaleziony, **_lsearch —** dodaje go do końca tablicy i zwiększa *numer*.

*Porównania* argument jest wskaźnik do procedury dostarczone przez użytkownika, który porównuje dwa elementy tablicy i zwraca wartość określającą ich relacji. **_lsearch —** wywołania *porównania* rutynowych jeden lub więcej razy podczas wyszukiwania przekazywanie wskaźników do dwóch elementów tablicy przy każdym wywołaniu. *Porównaj* należy porównać elementy i zwracać różną od zera (to znaczy elementy są inne) lub wartość 0 (tzn. elementy są identyczne).

Ta funkcja weryfikuje jego parametrów. Jeśli *porównania*, *klucza* lub *numer* jest **NULL**, lub jeśli *podstawowej* jest **NULL**i *numer* jest różna od zera, lub jeśli *szerokość* jest mniejsza od zera, zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i funkcja zwraca **NULL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lsearch**|\<Search.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
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

## <a name="see-also"></a>Zobacz także

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
