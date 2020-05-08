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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 4721ba96e145b3c2fde4ce0bb73157bbbcab4dff
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916459"
---
# <a name="_lfind"></a>_lfind

Wykonuje wyszukiwanie liniowe dla określonego klucza. Dostępna jest bezpieczniejsza wersja tej funkcji; Zobacz [_lfind_s](lfind-s.md).

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

*głównych*<br/>
Obiekt do wyszukania.

*base*<br/>
Wskaźnik do podstawy wyszukiwania danych.

*Liczba*<br/>
Liczba elementów tablicy.

*Szerokość*<br/>
Szerokość elementów tablicy.

*porównaniu*<br/>
Wskaźnik do procedury porównania. Pierwszy parametr jest wskaźnikiem do klucza do wyszukania. Drugi parametr jest wskaźnikiem do elementu tablicy, który będzie porównywany z kluczem.

## <a name="return-value"></a>Wartość zwracana

Jeśli klucz zostanie znaleziony, **_lfind** zwraca wskaźnik do elementu tablicy w *bazie* , który odpowiada *kluczowi*. Jeśli klucz nie zostanie znaleziony, **_lfind** zwraca **wartość null**.

## <a name="remarks"></a>Uwagi

Funkcja **_lfind** wykonuje wyszukiwanie liniowe dla *klucza* wartości w tablicy elementów *liczbowych* , każda z bajtów o *szerokości* . W przeciwieństwie do **bsearch**, **_lfind** nie wymaga sortowania tablicy. Argument *podstawowy* jest wskaźnikiem do podstawy tablicy do przeszukania. Argument *Compare* jest wskaźnikiem do procedury dostarczonej przez użytkownika, która porównuje dwa elementy tablicy, a następnie zwraca wartość określającą ich relację. **_lfind** wywołuje procedurę *Compare* jeden lub więcej razy podczas wyszukiwania, przekazując wskaźniki do dwóch elementów tablicy dla każdego wywołania. Procedura *Compare* musi porównać elementy, a następnie zwracać wartość różną od zera (oznacza to, że elementy są różne) lub 0 (oznacza to, że elementy są identyczne).

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *Compare*, *Key* lub *Number* ma **wartość null**lub jeśli *podstawa* ma **wartość null** , a *Liczba* jest różna od zera, lub jeśli *Szerokość* jest mniejsza od zera, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca **wartość null**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lfind**|\<Wyszukaj. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
