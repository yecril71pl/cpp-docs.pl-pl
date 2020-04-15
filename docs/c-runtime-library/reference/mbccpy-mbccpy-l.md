---
title: _mbccpy, _mbccpy_l
ms.date: 4/2/2020
api_name:
- _mbccpy
- _mbccpy_l
- _o__mbccpy
- _o__mbccpy_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 45f93e370e11cf38fc17da3557b21c636fcbc623
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341263"
---
# <a name="_mbccpy-_mbccpy_l"></a>_mbccpy, _mbccpy_l

Kopiuje znak wielobajtowy z jednego ciągu do drugiego ciągu. Dostępne są bezpieczniejsze wersje tych funkcji; patrz [_mbccpy_s, _mbccpy_s_l](mbccpy-s-mbccpy-s-l.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Dest*<br/>
Skopiuj miejsce docelowe.

*src*<br/>
Znak wielobajtowy do skopiowania.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="remarks"></a>Uwagi

Funkcja **_mbccpy** kopiuje jeden znak wielobajtowy z *src* do *dest*.

Ta funkcja sprawdza poprawność jego parametrów. Jeśli **_mbccpy** jest przekazywana wskaźnik null dla *dest* lub *src*, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **EINVAL**.

**_mbccpy** używa bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych. **_mbccpy_l** jest identyczna **z _mbccpy** z tą różnicą, że **_mbccpy_l** używa ustawień regionalnych przekazanych dla zachowania zależnego od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

**Uwaga dotycząca zabezpieczeń** Użyj ciągu zakończonego wartością null. Ciąg zakończony z wartością null nie może przekraczać rozmiaru buforu docelowego. Aby uzyskać więcej informacji, zobacz [Unikanie przekroczenia buforu](/windows/win32/SecBP/avoiding-buffer-overruns). Problemy z przepełnieniem buforu są częstą metodą ataku systemu, co powoduje nieuzasadnione podniesienie uprawnień.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy**|Mapowanie do funkcji makra lub wbudowanej|**_mbccpy**|Mapowanie do funkcji makra lub wbudowanej|
|**_tccpy_l**|Nie dotyczy|**_mbccpy_l**|Nie dotyczy|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbccpy**|\<mbctype.h>|
|**_mbccpy_l**|\<mbctype.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
