---
title: _strdate_s, _wstrdate_s
description: _strdate_s i _wstrdate_s są bezpieczne wersje CRT funkcji _strdate i _wstrdate, które umieszczają bieżącą datę w buforze.
ms.date: 4/2/2020
api_name:
- _strdate_s
- _wstrdate_s
- _o__strdate_s
- _o__wstrdate_s
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _strdate_s
- wstrdate_s
- _wstrdate_s
- strdate_s
- _tstrdate_s
helpviewer_keywords:
- dates, copying
- tstrdate_s function
- wstrdate_s function
- _tstrdate_s function
- strdate_s function
- copying dates
- _strdate_s function
- _wstrdate_s function
ms.assetid: d41d8ea9-e5ce-40d4-864e-1ac29b455991
ms.openlocfilehash: b4d977ba3546eae17218c63b1786fd26c784d340
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359820"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s, _wstrdate_s

Skopiuj bieżącą datę systemową do buforu. Te funkcje są wersjami [_strdate, _wstrdate](strdate-wstrdate.md) z ulepszeniami zabezpieczeń, jak opisano w [programie Funkcje zabezpieczeń w programie CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _strdate_s(
   char *buffer,
   size_t size
);
errno_t _wstrdate_s(
   wchar_t *buffer,
   size_t size
);
template <size_t size>
errno_t _strdate_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrdate_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*Buforu*\
Wskaźnik do buforu, aby umieścić sformatowany ciąg daty.

*Rozmiar*\
Rozmiar buforu w jednostkach znakowych.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie. Zwracana wartość jest kodem błędu, jeśli występuje błąd. Kody błędów są zdefiniowane w ERRNO. H; zobacz tabelę poniżej, aby uzyskać dokładne błędy generowane przez tę funkcję. Aby uzyskać więcej informacji na temat kodów błędów, zobacz [errno](../../c-runtime-library/errno-constants.md).

## <a name="error-conditions"></a>Warunki błędu

|*Buforu*|*Rozmiar*|Zwraca|Zawartość *buforu*|
|--------------|------------------------|------------|--------------------------|
|**Null**|(dowolny)|**Einval**|Nie zmodyfikowano|
|Nie **NULL** (wskażając prawidłowy bufor)|0|**Einval**|Nie zmodyfikowano|
|Nie **NULL** (wskażając prawidłowy bufor)|0 < *rozmiar* < 9|**Einval**|Pusty ciąg znaków|
|Nie **NULL** (wskażając prawidłowy bufor)|*rozmiar* >= 9|0|Bieżąca data sformatowana zgodnie z uwagami|

## <a name="security-issues"></a>Problemy z zabezpieczeniami

Przekazywanie nieprawidłowej wartości innej niż NULL dla *buforu* powoduje naruszenie zasad dostępu, jeśli parametr *size* jest większy niż dziewięć.

Przekazywanie wartości dla *rozmiaru* większego niż rzeczywisty rozmiar *buforu* powoduje przepełnienie buforu.

## <a name="remarks"></a>Uwagi

Funkcje te zapewniają bezpieczniejsze wersje **_strdate** i **_wstrdate.** Funkcja **_strdate_s** kopiuje bieżącą datę systemową do buforu wskazywowego przez *bufor*. `mm/dd/yy`Jest sformatowany `mm` , gdzie jest dwucyfrowy miesiąc, `dd` jest dniem `yy` dwucyfrowym i jest ostatnimi dwiema cyframi roku. Na przykład ciąg `12/05/99` reprezentuje 5 grudnia 1999. Bufor musi mieć co najmniej dziewięć znaków.

**_wstrdate_s** jest szerokoznakową wersją **_strdate_s**; argument i zwraca wartość **_wstrdate_s** są ciągami znaków o szerokich znakach. Te funkcje zachowują się identycznie w przeciwnym razie.

Gdy *bufor* jest wskaźnikiem **NULL** lub *rozmiar* jest mniejszy niż dziewięć znaków, wywoływany jest nieprawidłowy program obsługi parametrów. Jest to opisane w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, aby kontynuować, te funkcje zwracają -1. **Ustawiają errno** na **Wartość błędu,** jeśli bufor ma **wartość NULL** lub jeśli *rozmiar* jest mniejszy lub równy 0. Lub **ustawiają errno** na **ERANGE,** jeśli *rozmiar* jest mniejszy niż 9.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu. Przeciążenia można wywnioskować długość buforu automatycznie, co eliminuje konieczność określenia argumentu *rozmiaru.* Mogą też automatycznie zastępować niezabezpieczane funkcje nowszymi, bezpieczniejszymi odpowiednikami. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Rutynowe mapowanie tekstu ogólnego:

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strdate**|\<> time.h|
|**_wstrdate**|\<time.h> lub \<wchar.h>|
|**_strdate_s**|\<> time.h|

## <a name="example"></a>Przykład

Zobacz przykład [czasu](time-time32-time64.md).

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)\
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)\
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)\
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)\
[czas, _time32, _time64](time-time32-time64.md)\
[_tzset](tzset.md)
