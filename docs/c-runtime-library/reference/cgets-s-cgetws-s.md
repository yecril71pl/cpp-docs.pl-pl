---
title: _cgets_s, _cgetws_s
ms.date: 11/04/2016
api_name:
- _cgetws_s
- _cgets_s
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
- api-ms-win-crt-conio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cgets_s
- cgets_s
- cgetws_s
- _cgetws_s
helpviewer_keywords:
- strings [C++], getting from console
- console, getting strings from
- _cgets_s function
- cget_s function
- _cgetws_s function
- cgetws_s function
ms.assetid: 38b74897-afe6-4dd9-a43f-36a3c0d72c5c
ms.openlocfilehash: be2acefcf907ca9b908fa7f439b6e245a5e103d8
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624767"
---
# <a name="_cgets_s-_cgetws_s"></a>_cgets_s, _cgetws_s

Pobiera ciąg znaków z konsoli. Te wersje systemów [_cgets i _cgetws](../../c-runtime-library/cgets-cgetws.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
errno_t _cgets_s(
   char *buffer,
   size_t numberOfElements,
   size_t *pSizeRead
);
errno_t _cgetws_s(
   wchar_t *buffer
   size_t numberOfElements,
   size_t *pSizeRead
);
template <size_t size>
errno_t _cgets_s(
   char (&buffer)[size],
   size_t *pSizeRead
); // C++ only
template <size_t size>
errno_t _cgetws_s(
   wchar_t (&buffer)[size],
   size_t *pSizeRead
); // C++ only
```

### <a name="parameters"></a>Parametry

*buforu*<br/>
Lokalizacja magazynu dla danych.

*numberOfElements*<br/>
Rozmiar buforu w znakach jednobajtowych lub szerokich, który jest również maksymalną liczbą znaków, które mają być odczytywane.

*pSizeRead*<br/>
Liczba znaków, które są faktycznie odczytywane.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana wynosi zero, jeśli to się powiedzie; w przeciwnym razie kod błędu w przypadku wystąpienia błędu.

### <a name="error-conditions"></a>Warunki błędów

|*buforu*|*numberOfElements*|*pSizeRead*|przesłać|Zawartość *buforu*|
|--------------|------------------------|-----------------|------------|--------------------------|
|**NULL**|Ile|Ile|**EINVAL**|n/d|
|Nie **ma wartości null**|zero|Ile|**EINVAL**|nie zmodyfikowano|
|Nie **ma wartości null**|Ile|**NULL**|**EINVAL**|ciąg o zerowej długości|

## <a name="remarks"></a>Uwagi

**_cgets_s** i **_cgetws_s** Odczytaj ciąg z konsoli programu i skopiuj ciąg (z terminatorem o wartości null) do *buforu*. **_cgetws_s** jest wersją znaków dwubajtowych funkcji; Oprócz rozmiaru znaku zachowanie tych dwóch funkcji jest identyczne. Maksymalny rozmiar ciągu do odczytu jest przenoszona jako parametr *NumberOfElements* . Ten rozmiar powinien zawierać dodatkowy znak dla kończącego się wartości null. Rzeczywista liczba odczytanych znaków jest umieszczana w *pSizeRead*.

Jeśli wystąpi błąd podczas operacji lub weryfikacji parametrów, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** i **EINVAL** jest zwracany.

W C++programie korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość bufora, eliminując tym samym konieczność określenia argumentu rozmiaru i mogą automatycznie zastąpić starsze, mniej bezpieczne funkcje z ich nowszymi, bardziej bezpiecznymi odpowiednikami. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cgetts_s**|**_cgets_s**|**_cgets_s**|**_cgetws_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_cgets_s**|\<CONIO. h >|
|**_cgetws_s**|\<CONIO. h > lub \<WCHAR. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[We/wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
