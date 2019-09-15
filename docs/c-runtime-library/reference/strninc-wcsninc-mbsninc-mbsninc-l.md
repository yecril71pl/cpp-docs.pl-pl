---
title: _strninc, _wcsninc, _mbsninc, _mbsninc_l
ms.date: 11/04/2016
api_name:
- _mbsninc
- _mbsninc_l
- _wcsninc
- _strninc
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
- api-ms-win-crt-multibyte-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strninc
- wcsninc
- mbsninc_l
- _strninc
- _tcsninc
- mbsninc
- _mbsninc_l
- _ftcsninc
- _wcsninc
- _mbsninc
helpviewer_keywords:
- _mbsninc_l function
- mbsninc function
- _strninc function
- tcsninc function
- wcsninc function
- _mbsninc function
- strninc function
- _wcsninc function
- mbsninc_l function
- _tcsninc function
ms.assetid: 6caace64-f9e4-48c0-afa8-ea51824ad723
ms.openlocfilehash: b03ca4c9515bd2c70a1ce2574850e23b3add44c5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947068"
---
# <a name="_strninc-_wcsninc-_mbsninc-_mbsninc_l"></a>_strninc, _wcsninc, _mbsninc, _mbsninc_l

Przesuwa wskaźnik ciągu o **n** znaków.

> [!IMPORTANT]
> **_mbsninc** i **_mbsninc_l** nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
char *_strninc(
   const char *str,
   size_t count
);
wchar_t *_wcsninc(
   const wchar_t *str,
   size_t count
);
unsigned char *_mbsninc(
   const unsigned char *str,
   size_t count
);
unsigned char *_mbsninc(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Ciąg źródłowy.

*liczbą*<br/>
Liczba znaków do zwiększenia wskaźnika ciągu.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wskaźnik do *str* po zwiększeniu *liczby* znaków lub **wartości null** , jeśli dostarczony *wskaźnik ma* **wartość null**. Jeśli *Liczba* jest większa lub równa liczbie znaków w *str*, wynik jest niezdefiniowany.

## <a name="remarks"></a>Uwagi

Funkcja **_mbsninc** zwiększa *str* według *liczby* znaków wielobajtowych. **_mbsninc** rozpoznaje sekwencje znaków wielobajtowych zgodnie z aktualnie używaną [stroną kodową](../../c-runtime-library/code-pages.md) .

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsninc**|**_strninc**|**_mbsninc**|**_wcsninc**|

**_strninc** i **_wcsninc** są ciągami znaków dwubajtowych i ciągami o szerokim znaku **_mbsninc**. **_wcsninc** i **_strninc** są dostępne tylko dla tego mapowania i nie powinny być używane w inny sposób. Aby uzyskać więcej informacji, zobacz [Korzystanie z mapowań tekstu ogólnego](../../c-runtime-library/using-generic-text-mappings.md) i [mapowań tekstu ogólnego](../../c-runtime-library/generic-text-mappings.md).

**_mbsninc_l** jest identyczny, z tą różnicą, że używa zamiast tego parametru ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsninc**|\<mbstring.h>|
|**_mbsninc_l**|\<mbstring.h>|
|**_strninc**|\<Używanie TCHAR. h >|
|**_wcsninc**|\<Używanie TCHAR. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_strdec, _wcsdec, _mbsdec, _mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strinc, _wcsinc, _mbsinc, _mbsinc_l](strinc-wcsinc-mbsinc-mbsinc-l.md)<br/>
[_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
