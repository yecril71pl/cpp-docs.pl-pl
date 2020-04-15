---
title: _lfind
ms.date: 4/2/2020
api_name:
- _lfind
- _o__lfind
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
- _lfind
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
ms.openlocfilehash: 287cbd8bc9cc567a4a0d5b9505d57098197bc545
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342175"
---
# <a name="_lfind"></a>_lfind

Wykonuje wyszukiwanie liniowe określonego klucza. Dostępna jest bezpieczniejsza wersja tej funkcji; patrz [_lfind_s](lfind-s.md).

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

*key*<br/>
Obiekt do wyszukania.

*base*<br/>
Wskaźnik do podstawy danych wyszukiwania.

*numer*<br/>
Liczba elementów tablicy.

*Szerokość*<br/>
Szerokość elementów tablicy.

*Porównać*<br/>
Wskaźnik do procedury porównania. Pierwszy parametr jest wskaźnikiem do klucza do wyszukiwania. Drugi parametr jest wskaźnikiem do elementu tablicy, który ma być porównywany z kluczem.

## <a name="return-value"></a>Wartość zwracana

Jeśli klucz zostanie znaleziony, **_lfind** zwraca wskaźnik do elementu tablicy u *podstawy,* który pasuje do *klucza*. Jeśli klucz nie zostanie znaleziony, **_lfind** zwraca **wartość NULL**.

## <a name="remarks"></a>Uwagi

Funkcja **_lfind** wykonuje liniowe wyszukiwanie *klucza* wartości w tablicy elementów *liczbowych,* *z* których każdy ma bajt szerokości. W przeciwieństwie do **bsearch** **, _lfind** nie wymaga tablicy do sortowania. Argument *podstawowy* jest wskaźnikiem do podstawy tablicy, która ma zostać przeszukana. Argument *porównania* jest wskaźnikiem do procedury dostarczonej przez użytkownika, która porównuje dwa elementy tablicy, a następnie zwraca wartość określającą ich relację. **_lfind** wywołuje *rutynowe porównywanie* jeden lub więcej razy podczas wyszukiwania, przekazując wskaźniki do dwóch elementów tablicy w każdym wywołaniu. Procedura *porównywania* musi porównać elementy, a następnie zwrócić różną wartośćzer (co oznacza, że elementy są różne) lub 0 (co oznacza, że elementy są identyczne).

Ta funkcja sprawdza poprawność jego parametrów. Jeśli *porównaj*, *klucz* lub *liczba* ma **wartość NULL**lub jeśli *podstawa* ma **wartość NULL,** a *liczba* jest niezerowa lub jeśli *szerokość* jest mniejsza niż zero, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w obszarze Sprawdzanie [poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **Wartość EINVAL,** a funkcja zwraca **wartość NULL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lfind**|\<> search.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
