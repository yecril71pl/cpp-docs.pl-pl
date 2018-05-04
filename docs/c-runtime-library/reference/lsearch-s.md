---
title: _lsearch_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12315350b62673abb0a838f9d30830354c58da73
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="lsearchs"></a>_lsearch_s

Wykonuje wyszukiwanie liniowe dla wartości. Wersja [_lsearch —](lsearch.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Wskaźnik do podstawy tablicy do wyszukania.

*Numer*<br/>
Liczba elementów.

*Rozmiar*<br/>
Rozmiar każdy element tablicy bajtów.

*Porównaj*<br/>
Wskaźnik do procedury porównania. Drugi parametr jest wskaźnik do klucza dla wyszukiwania. Trzeci parametr jest wskaźnik do elementu tablicy ma zostać porównane z kluczem.

*Kontekst*<br/>
Wskaźnik do obiektu, który mogą być używane w funkcji porównania.

## <a name="return-value"></a>Wartość zwracana

Jeśli *klucza* zostanie znaleziony, **_lsearch_s —** zwraca wskaźnik do elementu tablicy w *podstawowej* odpowiadającego *klucza*. Jeśli *klucza* nie zostanie znaleziony, **_lsearch_s —** zwraca wskaźnik do nowo dodany element na końcu tablicy.

Jeśli nieprawidłowe parametry są przekazywane do funkcji, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, następnie **errno** ustawiono **einval —** i funkcja zwraca **NULL**. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Warunki błędów

|*Klucz*|*base*|*Porównaj*|*Numer*|*Rozmiar*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**NULL**|wszystkie|wszystkie|wszystkie|wszystkie|**EINVAL —**|
|wszystkie|**NULL**|wszystkie|!= 0|wszystkie|**EINVAL —**|
|wszystkie|wszystkie|wszystkie|wszystkie|zero|**EINVAL —**|
|wszystkie|wszystkie|**NULL**|Wystąpił|wszystkie|**EINVAL —**|

## <a name="remarks"></a>Uwagi

**_Lsearch_s —** funkcja wykonuje wyszukiwanie liniowe dla wartości *klucza* w tablicy *numer* z elementów *szerokość* bajtów. W odróżnieniu od **bsearch_s —**, **_lsearch_s —** nie wymaga tablicy ma zostać posortowana. Jeśli *klucza* nie zostanie znaleziony, następnie **_lsearch_s —** dodaje go do końca tablicy i zwiększa *numer*.

*Porównania* funkcji jest wskaźnikiem do procedury dostarczone przez użytkownika, który porównuje dwa elementy tablicy i zwraca wartość określającą ich relacji. *Porównania* funkcja przyjmuje również wskaźnik do kontekstu jako pierwszego argumentu. **_lsearch_s —** wywołania *porównania* jeden lub więcej razy podczas wyszukiwania przekazywanie wskaźników do dwóch elementów tablicy przy każdym wywołaniu. *Porównaj* należy porównać elementy, a następnie wróć albo różną od zera (to znaczy elementy są inne) lub wartość 0 (tzn. elementy są identyczne).

*Kontekstu* wskaźnika może być przydatna, jeśli struktura przeszukane danych jest częścią obiektu i *porównania* funkcji ma dostęp do elementów członkowskich obiektu. Na przykład kodu w *porównania* funkcji można rzutować wskaźnika void do odpowiedniego obiektu członków typu i dostępu do tego obiektu. Dodanie *kontekstu* sprawia, że wskaźnik **_lsearch_s —** bardziej bezpieczne, ponieważ dodatkowy kontekst mogą zostać użyte w celu uniknięcia ponownego rozpoczęcia błędów związanych z użyciem zmienne statyczne, aby udostępnić dane *porównania* funkcji.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lsearch_s**|\<Search.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
