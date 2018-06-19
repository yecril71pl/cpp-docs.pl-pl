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
ms.openlocfilehash: d79ab8362eaa911b7a4aa936d6351aa29f610fa8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403173"
---
# <a name="mbccpy-mbccpyl"></a>_mbccpy, _mbccpy_l

Kopiuje znaków wielobajtowych z jednego ciągu na inny ciąg. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_mbccpy_s —, _mbccpy_s_l —](mbccpy-s-mbccpy-s-l.md).

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*docelowy* lokalizacji docelowej kopiowania.

*SRC* znaków wielobajtowych do skopiowania.

*Ustawienia regionalne* ustawienia regionalne do użycia.

## <a name="remarks"></a>Uwagi

**_Mbccpy —** funkcja kopiuje znaków wielobajtowych jednego z *src* do *dest*.

Ta funkcja weryfikuje jego parametrów. Jeśli **_mbccpy —** jest przekazywany wskaźnika o wartości null *dest* lub *src*, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —**.

**_mbccpy —** używa bieżące ustawienia regionalne dla dowolnego zachowanie zależnych od ustawień regionalnych. **_mbccpy_l —** jest taka sama jak **_mbccpy —** z tą różnicą, że **_mbccpy_l —** korzysta z ustawień regionalnych przekazano wszystkie działania zależne od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

**Uwaga dotycząca zabezpieczeń** użyć ciągu zakończonego wartością null. Ciąg znaków zakończony znakiem null nie może przekraczać rozmiar buforu docelowego. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795). Przepełnienie buforu problemy używanej metody ataku systemu, co powoduje nieuzasadnione podniesienie uprawnień.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy —**|Map — makro lub wewnętrznej funkcji|**_mbccpy**|Map — makro lub wewnętrznej funkcji|
|**_tccpy_l —**|n/d|**_mbccpy_l**|n/d|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbccpy**|\<mbctype.h>|
|**_mbccpy_l**|\<mbctype.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
