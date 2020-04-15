---
title: _cgets_s, _cgetws_s
ms.date: 4/2/2020
api_name:
- _cgetws_s
- _cgets_s
- _o__cgets_s
- _o__cgetws_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b4871ff2c362e2c6cbe37be6a31bde4e6e258709
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333543"
---
# <a name="_cgets_s-_cgetws_s"></a>_cgets_s, _cgetws_s

Pobiera ciąg znaków z konsoli. Te wersje [_cgets i _cgetws](../../c-runtime-library/cgets-cgetws.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w funkcji zabezpieczeń w [CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Buforu*<br/>
Lokalizacja przechowywania danych.

*liczbaOfElements*<br/>
Rozmiar buforu w postaci jedno bajtowej lub szerokiej, co jest również maksymalną liczbą znaków do odczytu.

*pSizeCzysz*<br/>
Liczba znaków faktycznie przeczytanych.

## <a name="return-value"></a>Wartość zwracana

Zwracana wartość wynosi zero, jeśli zakończy się pomyślnie; w przeciwnym razie kod błędu, jeśli wystąpi błąd.

### <a name="error-conditions"></a>Warunki błędu

|*Buforu*|*liczbaOfElements*|*pSizeCzysz*|Zwraca|Zawartość *buforu*|
|--------------|------------------------|-----------------|------------|--------------------------|
|**Null**|Wszelki|Wszelki|**Einval**|Nie dotyczy|
|nie **NULL**|zero|Wszelki|**Einval**|nie zmodyfikowano|
|nie **NULL**|Wszelki|**Null**|**Einval**|ciąg o zerowej długości|

## <a name="remarks"></a>Uwagi

**_cgets_s** i **_cgetws_s** odczytać ciąg z konsoli i skopiować ciąg (z zerowym terminatorem) do *buforu*. **_cgetws_s** jest szeroka wersja znaku funkcji; poza rozmiarem znaku zachowanie tych dwóch funkcji jest identyczne. Maksymalny rozmiar ciągu do odczytu jest przekazywany jako *parametr numberOfElements.* Ten rozmiar powinien zawierać dodatkowy znak dla zakończenia null. Rzeczywista liczba odczytanych znaków jest umieszczana w *pSizeRead*.

Jeśli podczas operacji lub sprawdzania poprawności parametrów wystąpi błąd, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w obszarze [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **EINVAL** i **EINVAL** jest zwracany.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie, eliminując w ten sposób konieczność określenia argumentu rozmiaru i mogą automatycznie zastąpić starsze, mniej bezpieczne funkcje z ich nowszych, bardziej bezpiecznych odpowiedników. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cgetts_s**|**_cgets_s**|**_cgets_s**|**_cgetws_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_cgets_s**|\<> conio.h|
|**_cgetws_s**|\<conio.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Operacje We/Wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
