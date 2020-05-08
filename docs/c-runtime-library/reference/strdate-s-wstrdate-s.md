---
title: _strdate_s, _wstrdate_s
description: _strdate_s i _wstrdate_s są bezpiecznymi wersjami CRT _strdate i _wstrdate funkcje, które umieszczają bieżącą datę w buforze.
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 7fe8d682ab515d5a11e90f0c26e956725644806e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916912"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s, _wstrdate_s

Skopiuj bieżącą datę systemową do buforu. Te funkcje są wersjami [_strdate, _wstrdate](strdate-wstrdate.md) z ulepszonymi zabezpieczeniami, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*buforu*\
Wskaźnik do buforu służący do umieszczenia sformatowanego ciągu daty.

*zmienia*\
Rozmiar buforu w jednostkach znakowych.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli powodzenie. Wartość zwracana jest kodem błędu w przypadku wystąpienia błędu. Kody błędów są zdefiniowane w ERRNO. C w poniższej tabeli przedstawiono dokładne błędy wygenerowane przez tę funkcję. Aby uzyskać więcej informacji na temat kodów błędów, zobacz [errno](../../c-runtime-library/errno-constants.md).

## <a name="error-conditions"></a>Warunki błędów

|*buforu*|*size*|Przesłać|Zawartość *buforu*|
|--------------|------------------------|------------|--------------------------|
|**NULL**|ile|**EINVAL**|Nie zmodyfikowano|
|Nie **ma wartości null** (wskazuje na prawidłowy bufor)|0|**EINVAL**|Nie zmodyfikowano|
|Nie **ma wartości null** (wskazuje na prawidłowy bufor)|0 < *rozmiar* < 9|**EINVAL**|Pusty ciąg|
|Nie **ma wartości null** (wskazuje na prawidłowy bufor)|*rozmiar* >= 9|0|Bieżąca data sformatowana zgodnie z opisem w uwagach|

## <a name="security-issues"></a>Problemy z zabezpieczeniami

Przekazywanie w nieprawidłowej wartości innej niż NULL dla *buforu* powoduje naruszenie zasad dostępu, jeśli parametr *size* jest większy niż dziewięć.

Przekazywanie wartości *rozmiaru* większego niż rzeczywisty rozmiar *buforu* powoduje przepełnienie buforu.

## <a name="remarks"></a>Uwagi

Te funkcje zapewniają bezpieczniejsze wersje **_strdate** i **_wstrdate**. Funkcja **_strdate_s** kopiuje bieżącą datę systemową do buforu wskazywanym przez *bufor*. Jest on sformatowany `mm/dd/yy`, gdzie `mm` jest miesiąc dwucyfrowy, `dd` jest dwucyfrowym dniem i `yy` jest ostatnimi dwiema cyframi roku. Na przykład ciąg `12/05/99` reprezentuje 5 grudnia 1999. Długość buforu musi wynosić co najmniej dziewięć znaków.

**_wstrdate_s** to dwubajtowa wersja **_strdate_s**; argument i zwracana wartość **_wstrdate_s** są ciągami znaków dwubajtowych. Funkcje te zachowują się identycznie w inny sposób.

Gdy *bufor* jest wskaźnikiem o **wartości null** lub *rozmiar* jest krótszy niż dziewięć znaków, zostanie wywołana procedura obsługi nieprawidłowego parametru. Jest on opisany w temacie [Walidacja parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają-1. Ustawili **errno** na **EINVAL** , jeśli bufor ma **wartość null** lub jeśli *rozmiar* jest mniejszy lub równy 0. Lub ustawiają **errno** na **ERANGE** , jeśli *rozmiar* jest mniejszy niż 9.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów. Przeciążenia mogą automatycznie wywnioskować długość buforu, co eliminuje konieczność określenia argumentu *rozmiaru* . Ponadto mogą automatycznie zastąpić funkcje niezabezpieczone nowszymi, bardziej bezpiecznymi odpowiednikami. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Mapowanie procedury tekstu ogólnego:

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strdate**|\<> godziny. h|
|**_wstrdate**|\<Time. h> lub \<WCHAR. h>|
|**_strdate_s**|\<> godziny. h|

## <a name="example"></a>Przykład

Zobacz przykład [czasu](time-time32-time64.md).

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)\
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)\
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)\
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)\
[godzina, _time32, _time64](time-time32-time64.md)\
[_tzset](tzset.md)
