---
title: _lsearch
ms.date: 11/04/2016
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
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
ms.openlocfilehash: 340e8ac382972b15acc52013d5d6a51352db969c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285659"
---
# <a name="lsearch"></a>_lsearch

Wykonuje wyszukiwanie liniowe dla wartości; dodaje do końca listy Jeśli nie zostanie znaleziony. Bardziej bezpieczna wersja ta funkcja jest dostępna; zobacz [_lsearch_s —](lsearch-s.md).

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
Wskaźnik do podstawowego tablicy ma być przeszukiwany.

*Numer*<br/>
Liczba elementów.

*width*<br/>
Szerokość każdego elementu tablicy.

*compare*<br/>
Wskaźnik do procedury porównania. Pierwszy parametr jest wskaźnikiem do klucza dla wyszukiwania. Drugi parametr jest wskaźnik do elementu tablicy, który można porównać z kluczem.

## <a name="return-value"></a>Wartość zwracana

Jeśli klucz zostanie znaleziony, **_lsearch —** zwraca wskaźnik do elementu tablicy, od *podstawowy* odpowiadający *klucz*. Jeśli klucz nie zostanie znaleziony, **_lsearch —** zwraca wskaźnik do elementu nowo dodanym na końcu tablicy.

## <a name="remarks"></a>Uwagi

**_Lsearch —** funkcja wykonuje wyszukiwanie liniowe dla wartości *klucz* tablicę *numer* elementów, z których każdy z *szerokość* bajtów. W odróżnieniu od **bsearch —**, **_lsearch —** nie wymaga tablicy, która ma zostać posortowana. Jeśli *klucz* nie zostanie znaleziony, **_lsearch —** dodaje go do końca tablicy i zwiększa *numer*.

*Porównania* argument jest wskaźnikiem do procedury dostarczone przez użytkownika, która porównuje dwa elementy tablicy i zwraca wartość określającą ich relacje. **_lsearch —** wywołania *porównania* rutynowych jeden lub więcej razy podczas wyszukiwania, przekazując wskaźniki do dwóch elementów tablicy przy każdym wywołaniu. *Porównaj* należy porównać elementów i zwracać wartość różną od zera (tzn. elementy są różnych) lub od 0 (co oznacza, że elementy są identyczne).

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *porównania*, *klucz* lub *numer* jest **NULL**, lub jeśli *podstawowy* jest **NULL**i *numer* jest różna od zera, lub jeśli *szerokość* jest mniejsza niż zero, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca **NULL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lsearch**|\<Search.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
