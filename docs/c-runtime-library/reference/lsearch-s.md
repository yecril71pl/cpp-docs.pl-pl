---
title: _lsearch_s
ms.date: 4/2/2020
api_name:
- _lsearch_s
- _o__lsearch_s
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
ms.openlocfilehash: 720b83dd48b42d77f35bce12f16e8ac79eb3b4d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341648"
---
# <a name="_lsearch_s"></a>_lsearch_s

Wykonuje wyszukiwanie liniowe wartości. Wersja [_lsearch](lsearch.md) z ulepszeniami zabezpieczeń, jak opisano w [obszarze Funkcje zabezpieczeń w crt](../../c-runtime-library/security-features-in-the-crt.md).

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

*key*<br/>
Obiekt do wyszukania.

*base*<br/>
Wskaźnik do podstawy tablicy do przeszukania.

*numer*<br/>
Liczba elementów.

*Rozmiar*<br/>
Rozmiar każdego elementu tablicy w bajtach.

*Porównać*<br/>
Wskaźnik do procedury porównania. Drugi parametr jest wskaźnikiem do klucza wyszukiwania. Trzeci parametr jest wskaźnikiem do elementu tablicy, który ma być porównywany z kluczem.

*Kontekście*<br/>
Wskaźnik do obiektu, który może być dostępny w funkcji porównania.

## <a name="return-value"></a>Wartość zwracana

Jeśli zostanie znaleziony *klucz,* **_lsearch_s** zwraca wskaźnik do elementu tablicy u *podstawy,* który pasuje do *klucza*. Jeśli *klucz* nie zostanie znaleziony, **_lsearch_s** zwraca wskaźnik do nowo dodanego elementu na końcu tablicy.

Jeśli nieprawidłowe parametry są przekazywane do funkcji, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **Wartość EINVAL,** a funkcja zwraca **wartość NULL**. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Warunki błędu

|*key*|*base*|*Porównać*|*numer*|*Rozmiar*|**Errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**Null**|Wszelki|Wszelki|Wszelki|Wszelki|**Einval**|
|Wszelki|**Null**|Wszelki|!= 0|Wszelki|**Einval**|
|Wszelki|Wszelki|Wszelki|Wszelki|zero|**Einval**|
|Wszelki|Wszelki|**Null**|an|Wszelki|**Einval**|

## <a name="remarks"></a>Uwagi

Funkcja **_lsearch_s** wykonuje liniowe wyszukiwanie *klucza* wartości w tablicy elementów *liczbowych,* z których każdy bajtów *szerokości.* W przeciwieństwie do **bsearch_s** **_lsearch_s** nie wymaga sortowania tablicy. Jeśli *klucz* nie zostanie znaleziony, **_lsearch_s** dodaje go na końcu tablicy i zwiększa *liczbę*.

Funkcja *porównywania* jest wskaźnikiem do procedury dostarczonej przez użytkownika, która porównuje dwa elementy tablicy i zwraca wartość określającą ich relację. Funkcja *porównywania* przyjmuje również wskaźnik do kontekstu jako pierwszy argument. **_lsearch_s** *wywołania porównać* jeden lub więcej razy podczas wyszukiwania, przekazywanie wskaźników do dwóch elementów tablicy na każde wywołanie. *compare* musi porównać elementy, a następnie zwrócić nonzero (co oznacza, że elementy są różne) lub 0 (co oznacza, że elementy są identyczne).

Wskaźnik *kontekstu* może być przydatne, jeśli przeszukiwana struktura danych jest częścią obiektu i *funkcja porównania* musi uzyskać dostęp do elementów członkowskich obiektu. Na przykład kod w funkcji *porównywania* można rzutować wskaźnik void do odpowiedniego typu obiektu i uzyskać dostęp do elementów członkowskich tego obiektu. Dodanie wskaźnika *kontekstu* sprawia, **że _lsearch_s** bardziej bezpieczne, ponieważ dodatkowy kontekst może służyć do uniknięcia błędów reentrancy skojarzone z przy użyciu zmiennych statycznych, aby udostępnić dane do funkcji *porównania.*

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lsearch_s**|\<> search.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
