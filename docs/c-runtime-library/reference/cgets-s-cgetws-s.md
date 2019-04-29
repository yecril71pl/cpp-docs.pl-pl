---
title: _cgets_s, _cgetws_s
ms.date: 11/04/2016
apiname:
- _cgetws_s
- _cgets_s
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 8341b775df3b9cbaececdfaa1f17e075d7c7416c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340588"
---
# <a name="cgetss-cgetwss"></a>_cgets_s, _cgetws_s

Pobiera ciąg znaków z konsoli. Te wersje [_cgets i _cgetws —](../../c-runtime-library/cgets-cgetws.md) mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*buffer*<br/>
Lokalizacja magazynowa danych.

*numberOfElements*<br/>
Rozmiar buforu znaków jednobajtowych lub szerokie, która jest również maksymalna liczba znaków do odczytania.

*pSizeRead*<br/>
Liczba znaków rzeczywiście odczytu.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana wynosi zero, jeśli to się powiedzie; w przeciwnym razie kod błędu, jeśli wystąpi błąd.

### <a name="error-conditions"></a>Warunki błędów

|*buffer*|*numberOfElements*|*pSizeRead*|Wróć|Zawartość *buforu*|
|--------------|------------------------|-----------------|------------|--------------------------|
|**NULL**|Wszystkie|Wszystkie|**EINVAL**|n/d|
|Nie **o wartości NULL**|zero|Wszystkie|**EINVAL**|Nie zmodyfikowano|
|Nie **o wartości NULL**|Wszystkie|**NULL**|**EINVAL**|Ciąg o zerowej długości|

## <a name="remarks"></a>Uwagi

**_cgets_s** i **_cgetws_s —** odczytują ciąg z konsoli i skopiuj ciąg (z terminatorem null) do *buforu*. **_cgetws_s —** to wersja znaku dwubajtowego funkcji; inne niż rozmiar znaków zachowanie te dwie funkcje są identyczne. Maksymalny rozmiar ciągu do odczytu jest przekazywany jako *numberOfElements* parametru. Ten rozmiar powinien zawierać dodatkowy znak dla zakończenia o wartości null. Rzeczywista liczba znaków czytanych jest umieszczany w *pSizeRead*.

Jeśli wystąpi błąd podczas operacji lub Sprawdzanie poprawności parametrów, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** i **EINVAL** jest zwracana.

W języku C++ korzystania z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia może wywnioskować długość buforu automatycznie, a tym samym, eliminując konieczność określenia argumentu rozmiaru, a te mogą automatycznie zastąpić starsze, mniej bezpieczne funkcje z ich nowszymi, bardziej bezpiecznymi odpowiednikami. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cgetts_s**|**_cgets_s**|**_cgets_s**|**_cgetws_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_cgets_s**|\<conio.h>|
|**_cgetws_s**|\<conio.h > lub \<wchar.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[We/Wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
