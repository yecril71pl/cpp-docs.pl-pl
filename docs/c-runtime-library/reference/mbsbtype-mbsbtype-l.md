---
title: _mbsbtype —, _mbsbtype_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsbtype_l
- _mbsbtype
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
dev_langs:
- C++
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be098cb1fe53e1345f0c4f40212657f4bfd97f4f
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="mbsbtype-mbsbtypel"></a>_mbsbtype, _mbsbtype_l

Zwraca typ bajtów ciągu.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _mbsbtype(
   const unsigned char *mbstr,
   size_t count
);
int _mbsbtype_l(
   const unsigned char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*mbstr*<br/>
Adres sekwencji znaków wielobajtowych.

*Liczba*<br/>
Przesunięcie bajtów, z węzła głównego w ciągu.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbsbtype —** i **_mbsbtype_l —** zwraca wartość wskazująca wynik testu w określonym bajcie. Stałe manifestu w poniższej tabeli są definiowane w Mbctype.h.

|Wartość zwracana|Byte — typ|
|------------------|---------------|
|**_MBC_SINGLE** (0)|Znaki jednobajtowe. Na przykład w strona kodowa 932 **_mbsbtype —** zwraca wartość 0, jeśli w określonym bajcie znajduje się w zakresie wartości 0x20-0x7E lub 0xA1 - 0xDF.|
|**_MBC_LEAD** (1)|Prowadzić bajtów znaków wielobajtowych. Na przykład w strona kodowa 932 **_mbsbtype —** zwraca wartość 1, jeśli w określonym bajcie znajduje się w zakresie 0x81-0x9F lub wartość 0xE0 - 0xFC.|
|**_MBC_TRAIL** (2)|Końcowy bajtów znaków wielobajtowych. Na przykład w strona kodowa 932 **_mbsbtype —** zwraca 2, jeśli w określonym bajcie znajduje się w zakresie 0x40-0x7E lub 0x80 - 0xFC.|
|**_MBC_ILLEGAL** (-1)|**Wartość NULL** ciągu, nieprawidłowy znak lub null bajtów znaleziono przed bajtów przy przesunięciu *liczba* w *mbstr*.|

## <a name="remarks"></a>Uwagi

**_Mbsbtype —** funkcja określa typ bajtów w ciąg znaków wielobajtowych. Funkcja sprawdza, czy tylko bajtów przy przesunięciu *liczba* w *mbstr*, ignorowanie nieprawidłowe znaki, przed określonym bajcie.

Wartość wyjściowa jest zagrożony ustawienie **lc_ctype —** ustawienie kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersja tej funkcji bez **_l** sufiks używa bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersja z **_l** sufiks jest identyczny z tą różnicą, że wykorzystuje ona przekazany parametr ustawień regionalnych w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Jeśli ciąg wejściowy jest **NULL**, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i funkcja zwraca **_MBC_ILLEGAL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Dla manifest stałe używane jako wartości zwracanych.

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
