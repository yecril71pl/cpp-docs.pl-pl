---
title: _lsearch_s
ms.date: 11/04/2016
apiname:
- _lsearch_s
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
- _lsearch_s
- lsearch_s
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
ms.openlocfilehash: f57a96622419e3f72fc2df5b260cbbbdd59666ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677009"
---
# <a name="lsearchs"></a>_lsearch_s

Wykonuje wyszukiwanie liniowe dla wartości. Wersja [_lsearch —](lsearch.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
void *_lsearch_s(
   const void *key,
   void *base,
   unsigned int *num,
   size_t size,
   int (__cdecl *compare)(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Obiekt do wyszukania.

*base*<br/>
Wskaźnik do podstawowego tablicy ma być przeszukiwany.

*Numer*<br/>
Liczba elementów.

*Rozmiar*<br/>
Rozmiar każdego elementu tablicy, w bajtach.

*Porównanie*<br/>
Wskaźnik do procedury porównania. Drugi parametr jest wskaźnikiem do klucza dla wyszukiwania. Trzeci parametr jest wskaźnik do elementu tablicy, który można porównać z kluczem.

*Kontekst*<br/>
Wskaźnik do obiektu, który może być uzyskiwany w funkcji porównywania.

## <a name="return-value"></a>Wartość zwracana

Jeśli *klucz* zostanie znaleziony, **_lsearch_s —** zwraca wskaźnik do elementu tablicy, od *podstawowy* odpowiadający *klucz*. Jeśli *klucz* nie zostanie znaleziony, **_lsearch_s —** zwraca wskaźnik do elementu nowo dodanym na końcu tablicy.

Jeśli nieprawidłowe parametry są przekazywane do funkcji, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, następnie **errno** ustawiono **EINVAL** a funkcja zwraca **NULL**. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Warunki błędów

|*Klucz*|*base*|*Porównanie*|*Numer*|*Rozmiar*|**numer błędu**|
|-----------|------------|---------------|-----------|------------|-------------|
|**NULL**|Wszystkie|Wszystkie|Wszystkie|Wszystkie|**EINVAL**|
|Wszystkie|**NULL**|Wszystkie|!= 0|Wszystkie|**EINVAL**|
|Wszystkie|Wszystkie|Wszystkie|Wszystkie|zero|**EINVAL**|
|Wszystkie|Wszystkie|**NULL**|Usługi|Wszystkie|**EINVAL**|

## <a name="remarks"></a>Uwagi

**_Lsearch_s —** funkcja wykonuje wyszukiwanie liniowe dla wartości *klucz* tablicę *numer* elementów, z których każdy z *szerokość* bajtów. W odróżnieniu od **bsearch_s —**, **_lsearch_s —** nie wymaga tablicy, która ma zostać posortowana. Jeśli *klucz* nie zostanie znaleziony, następnie **_lsearch_s —** dodaje go do końca tablicy i zwiększa *numer*.

*Porównania* funkcji jest wskaźnikiem do procedury dostarczone przez użytkownika, która porównuje dwa elementy tablicy i zwraca wartość określającą ich relacje. *Porównania* funkcja również przyjmuje wskaźnik do kontekstu, który jako pierwszy argument. **_lsearch_s —** wywołania *porównania* jeden lub więcej razy podczas wyszukiwania, przekazując wskaźniki do dwóch elementów tablicy przy każdym wywołaniu. *Porównaj* należy porównać elementów, a następnie wróć albo wartość różną od zera (tzn. elementy są różnych) lub od 0 (co oznacza, że elementy są identyczne).

*Kontekstu* wskaźnik może być przydatne, jeśli struktura wyszukiwanych danych jest częścią obiektu i *porównania* funkcji ma dostęp do elementów członkowskich obiektu. Na przykład, możesz pisać kod w *porównania* funkcji można rzutować wskaźnika void do odpowiedniego obiektu typu i dostęp do elementów członkowskich tego obiektu. Dodanie *kontekstu* sprawia, że wskaźnik **_lsearch_s —** bezpieczniejsze, ponieważ dodatkowy kontekst można uniknąć błędów współużytkowania wątkowości, związanych z użyciem statyczne zmienne, aby udostępnić dane *porównania* funkcji.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lsearch_s**|\<Search.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
