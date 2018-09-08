---
title: _mbccpy, _mbccpy_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ebc03a459a190144217ca15a9ab13bef395d5128
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103726"
---
# <a name="mbccpy-mbccpyl"></a>_mbccpy, _mbccpy_l

Kopiuje znak wielobajtowy z jednego ciągu do innego ciągu. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [_mbccpy_s —, _mbccpy_s_l —](mbccpy-s-mbccpy-s-l.md).

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Miejsce docelowe kopii.

*src*<br/>
Znak wielobajtowy do skopiowania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="remarks"></a>Uwagi

**_Mbccpy —** funkcja kopiuje jeden znak wielobajtowy z *src* do *dest*.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli **_mbccpy —** jest przekazywany jest pusty wskaźnik *dest* lub *src*, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL**.

**_mbccpy —** używa bieżących ustawień regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych. **_mbccpy_l —** jest taka sama jak **_mbccpy —** z tą różnicą, że **_mbccpy_l —** korzysta z regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

**Uwaga dotycząca zabezpieczeń** Użyj ciąg zakończony znakiem null. Ciąg zakończony znakiem null nie może przekraczać rozmiaru bufora docelowego. Aby uzyskać więcej informacji, zobacz [unikanie przepełnień bufora](/windows/desktop/SecBP/avoiding-buffer-overruns). Problemy z przepełnieniem buforu są częstą metodą ataku systemu, co nieuzasadnione podniesienie poziomu uprawnień.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy —**|Mapy i makro lub funkcja śródwierszowa|**_mbccpy**|Mapy i makro lub funkcja śródwierszowa|
|**_tccpy_l —**|n/d|**_mbccpy_l**|n/d|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbccpy**|\<mbctype.h>|
|**_mbccpy_l**|\<mbctype.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
