---
title: _mbccpy, _mbccpy_l
ms.date: 11/04/2016
apiname:
- _mbccpy
- _mbccpy_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbccpy
- tccpy
- ftccpy
- mbccpy
- _tccpy
- _ftccpy
helpviewer_keywords:
- _tccpy function
- _tccpy_l function
- tccpy_l function
- tccpy function
- mbccpy function
- _mbccpy_l function
- _mbccpy function
- mbccpy_l function
ms.assetid: 13f4de6e-7792-41ac-b319-dd9b135433aa
ms.openlocfilehash: 8d0711a98813565e945dad1d0e998847029668c2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499897"
---
# <a name="_mbccpy-_mbccpy_l"></a>_mbccpy, _mbccpy_l

Kopiuje znak wielobajtowy z jednego ciągu do innego ciągu. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [_mbccpy_s, _mbccpy_s_l](mbccpy-s-mbccpy-s-l.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
void _mbccpy(
   unsigned char *dest,
   const unsigned char *src
);
void _mbccpy_l(
   unsigned char *dest,
   const unsigned char *src,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*dest*<br/>
Kopiuj miejsce docelowe.

*SRC*<br/>
Znak wielobajtowy do skopiowania.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="remarks"></a>Uwagi

Funkcja **_mbccpy** kopiuje jeden znak wielobajtowy z *src* do miejsca *docelowego*.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli **_mbccpy** jest przekazywać wskaźnik o wartości null dla elementu *docelowego* lub *src*, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL**.

**_mbccpy** używa bieżących ustawień regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych. **_mbccpy_l** jest taka sama jak **_mbccpy** , z wyjątkiem tego, że **_mbccpy_l** korzysta z ustawień regionalnych przewidzianych dla wszelkich zachowań zależnych od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

**Uwaga dotycząca zabezpieczeń** Użyj ciągu zakończenia o wartości null. Ciąg zakończony znakiem null nie może przekraczać rozmiaru buforu docelowego. Aby uzyskać więcej informacji, zobacz Unikanie przekroczeń [buforu](/windows/win32/SecBP/avoiding-buffer-overruns). Problemy związane z przepełnieniem buforu są częstą metodą ataku systemu, powodując nieuzasadnione podniesienie uprawnień.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy**|Mapuje na makro lub funkcję wbudowaną|**_mbccpy**|Mapuje na makro lub funkcję wbudowaną|
|**_tccpy_l**|n/d|**_mbccpy_l**|n/d|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbccpy**|\<mbctype.h>|
|**_mbccpy_l**|\<mbctype.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
