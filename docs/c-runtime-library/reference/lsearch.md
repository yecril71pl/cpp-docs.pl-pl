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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 73bc82ed57692dee348448d2b523961324203ca9
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911331"
---
# <a name="_lsearch"></a>_lsearch

Wykonuje wyszukiwanie liniowe dla wartości; dodaje do końca listy, jeśli nie zostanie znaleziona. Dostępna jest bezpieczniejsza wersja tej funkcji; Zobacz [_lsearch_s](lsearch-s.md).

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

*głównych*<br/>
Obiekt do wyszukania.

*base*<br/>
Wskaźnik na podstawę tablicy do przeszukania.

*Liczba*<br/>
Liczba elementów.

*Szerokość*<br/>
Szerokość każdego elementu tablicy.

*porównaniu*<br/>
Wskaźnik do procedury porównania. Pierwszy parametr jest wskaźnikiem do klucza do wyszukania. Drugi parametr jest wskaźnikiem do elementu tablicy, który będzie porównywany z kluczem.

## <a name="return-value"></a>Wartość zwracana

Jeśli klucz zostanie znaleziony, **_lsearch** zwraca wskaźnik do elementu tablicy w *bazie* , który odpowiada *kluczowi*. Jeśli klucz nie zostanie znaleziony, **_lsearch** zwraca wskaźnik do nowo dodanego elementu na końcu tablicy.

## <a name="remarks"></a>Uwagi

Funkcja **_lsearch** wykonuje wyszukiwanie liniowe dla *klucza* wartości w tablicy elementów *liczbowych* , każda z bajtów o *szerokości* . W przeciwieństwie do **bsearch**, **_lsearch** nie wymaga sortowania tablicy. Jeśli nie odnaleziono *klucza* , **_lsearch** dodaje go na końcu tablicy i zwiększa *liczbę*.

Argument *Compare* jest wskaźnikiem do procedury dostarczonej przez użytkownika, która porównuje dwa elementy tablicy i zwraca wartość określającą ich relację. **_lsearch** wywołuje procedurę *Compare* jeden lub więcej razy podczas wyszukiwania, przekazując wskaźniki do dwóch elementów tablicy dla każdego wywołania. *porównanie* musi porównać elementy i zwracać wartość różną od zera (oznacza to, że elementy są różne) lub 0 (oznacza to, że elementy są identyczne).

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *Compare*, *Key* lub *Number* ma **wartość null**lub jeśli *podstawa* ma **wartość null** , a *Liczba* jest różna od zera, lub jeśli *Szerokość* jest mniejsza od zera, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca **wartość null**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lsearch**|\<Wyszukaj. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
