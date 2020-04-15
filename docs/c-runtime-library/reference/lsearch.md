---
title: _lsearch
ms.date: 4/2/2020
api_name:
- _lsearch
- _o__lsearch
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
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _lsearch
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
ms.openlocfilehash: a6ef3d86ffe8f03da34d4a374bddda1452815672
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341635"
---
# <a name="_lsearch"></a>_lsearch

Wykonuje wyszukiwanie liniowe wartości; dodaje na koniec listy, jeśli nie znaleziono. Dostępna jest bezpieczniejsza wersja tej funkcji; patrz [_lsearch_s](lsearch-s.md).

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

*key*<br/>
Obiekt do wyszukania.

*base*<br/>
Wskaźnik do podstawy tablicy do przeszukania.

*numer*<br/>
Liczba elementów.

*Szerokość*<br/>
Szerokość każdego elementu tablicy.

*Porównać*<br/>
Wskaźnik do procedury porównania. Pierwszy parametr jest wskaźnikiem do klucza wyszukiwania. Drugi parametr jest wskaźnikiem do elementu tablicy, który ma być porównywany z kluczem.

## <a name="return-value"></a>Wartość zwracana

Jeśli klucz zostanie znaleziony, **_lsearch** zwraca wskaźnik do elementu tablicy u *podstawy,* który pasuje do *klucza*. Jeśli klucz nie zostanie znaleziony, **_lsearch** zwraca wskaźnik do nowo dodanego elementu na końcu tablicy.

## <a name="remarks"></a>Uwagi

Funkcja **_lsearch** wykonuje liniowe wyszukiwanie *klucza* wartości w tablicy elementów *liczbowych,* z których każdy bajtów *szerokości.* W przeciwieństwie do **bsearch** **, _lsearch** nie wymaga tablicy do sortowania. Jeśli *klucz* nie zostanie znaleziony, **_lsearch** dodaje go na końcu tablicy i zwiększa *liczbę*.

Argument *porównania* jest wskaźnikiem do procedury dostarczonej przez użytkownika, która porównuje dwa elementy tablicy i zwraca wartość określającą ich relację. **_lsearch** wywołuje *rutynowe porównywanie* jeden lub więcej razy podczas wyszukiwania, przekazując wskaźniki do dwóch elementów tablicy w każdym wywołaniu. *compare* musi porównać elementy i zwrócić nonzero (co oznacza, że elementy są różne) lub 0 (co oznacza, że elementy są identyczne).

Ta funkcja sprawdza poprawność jego parametrów. Jeśli *porównaj*, *klucz* lub *liczba* ma **wartość NULL**lub jeśli *podstawa* ma **wartość NULL,** a *liczba* jest niezerowa lub jeśli *szerokość* jest mniejsza niż zero, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w obszarze Sprawdzanie [poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **Wartość EINVAL,** a funkcja zwraca **wartość NULL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lsearch**|\<> search.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
