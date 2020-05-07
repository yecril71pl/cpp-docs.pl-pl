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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: d8c421eb3c7a6a617ce073cbf5f36416294c1874
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920447"
---
# <a name="_lsearch_s"></a>_lsearch_s

Wykonuje wyszukiwanie liniowe dla wartości. Wersja [_lsearch](lsearch.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*głównych*<br/>
Obiekt do wyszukania.

*base*<br/>
Wskaźnik na podstawę tablicy do przeszukania.

*Liczba*<br/>
Liczba elementów.

*size*<br/>
Rozmiar każdego elementu tablicy w bajtach.

*porównaniu*<br/>
Wskaźnik do procedury porównania. Drugi parametr jest wskaźnikiem do klucza do wyszukania. Trzeci parametr jest wskaźnikiem do elementu tablicy, który będzie porównywany z kluczem.

*Context*<br/>
Wskaźnik do obiektu, do którego można uzyskać dostęp w funkcji porównywania.

## <a name="return-value"></a>Wartość zwracana

Jeśli zostanie znaleziony *klucz* , **_lsearch_s** zwraca wskaźnik do elementu tablicy w *bazie* , który odpowiada *kluczowi*. Jeśli nie odnaleziono *klucza* , **_lsearch_s** zwraca wskaźnik do nowo dodanego elementu na końcu tablicy.

Jeśli do funkcji są przenoszone nieprawidłowe parametry, procedura obsługi nieprawidłowego parametru jest wywoływana, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca **wartość null**. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Warunki błędów

|*głównych*|*base*|*porównaniu*|*Liczba*|*size*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**NULL**|ile|ile|ile|ile|**EINVAL**|
|ile|**NULL**|ile|! = 0|ile|**EINVAL**|
|ile|ile|ile|ile|zero|**EINVAL**|
|ile|ile|**NULL**|an|ile|**EINVAL**|

## <a name="remarks"></a>Uwagi

Funkcja **_lsearch_s** wykonuje wyszukiwanie liniowe dla *klucza* wartości w tablicy elementów *liczbowych* , każda z bajtów o *szerokości* . W przeciwieństwie do **bsearch_s**, **_lsearch_s** nie wymaga sortowania tablicy. Jeśli nie odnaleziono *klucza* , **_lsearch_s** dodaje go na końcu tablicy i zwiększa *liczbę*.

Funkcja *Compare* jest wskaźnikiem do procedury dostarczonej przez użytkownika, która porównuje dwa elementy tablicy i zwraca wartość określającą ich relację. Funkcja *Compare* pobiera również wskaźnik do kontekstu jako pierwszy argument. **_lsearch_s** wywołania _lsearch_s *porównują* jeden lub więcej razy podczas wyszukiwania, przekazując wskaźniki do dwóch elementów tablicy dla każdego wywołania. *porównanie* musi porównać elementy, a następnie zwracać wartość różną od zera (co oznacza, że elementy są różne) lub 0 (oznacza to, że elementy są identyczne).

Wskaźnik *kontekstu* może być przydatny, jeśli przeszukiwana struktura danych jest częścią obiektu, a funkcja *porównywania* musi uzyskać dostęp do elementów członkowskich obiektu. Na przykład kod w funkcji *Compare* może rzutować wskaźnik void na odpowiedni typ obiektu i uzyskać dostęp do elementów członkowskich tego obiektu. Dodanie wskaźnika *kontekstu* ułatwia **_lsearch_s** bezpieczniejsze, ponieważ można użyć dodatkowego kontekstu, aby uniknąć współużytkowania wątkowości błędów skojarzonych z użyciem zmiennych statycznych w celu udostępnienia danych funkcji *Compare* .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lsearch_s**|\<Wyszukaj. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
