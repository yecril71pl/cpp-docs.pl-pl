---
title: _mbsbtype, _mbsbtype_l
ms.date: 11/04/2016
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
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
ms.openlocfilehash: 5c2927b4e4b68b1284341fe7e767ec50feb21a44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331509"
---
# <a name="mbsbtype-mbsbtypel"></a>_mbsbtype, _mbsbtype_l

Zwraca wartość typu bajtu wewnątrz ciągu.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Przesunięcie bajtu od czoła ciągu.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbsbtype —** i **_mbsbtype_l —** zwraca wartość całkowitą, wskazując wynik testu na określonym bajcie. Stałe manifestu w poniższej tabeli są zdefiniowane w Mbctype.h.

|Wartość zwracana|Byte — typ|
|------------------|---------------|
|**_MBC_SINGLE** (0)|Znak Jednobajtowy. Na przykład na stronie kodowej 932 **_mbsbtype —** zwraca wartość 0, jeśli określony bajt znajduje się w zakresie 0x20 — 0x7E lub 0xA1 - 0xDF.|
|**_MBC_LEAD** (1)|Bajt znaku wielobajtowego. Na przykład na stronie kodowej 932 **_mbsbtype —** zwraca wartość 1, jeśli określony bajt znajduje się w zakresie 0x81-0x9F lub wartość 0xE0 — 0xFC.|
|**_MBC_TRAIL** (2)|Bajt znaku wielobajtowego. Na przykład na stronie kodowej 932 **_mbsbtype —** zwraca wartość 2, jeśli określony bajt znajduje się w zakresie 0x40-0x7E lub 0x80 - 0xFC.|
|**_MBC_ILLEGAL** (-1)|**Wartość NULL** ciągu, nieprawidłowy znak lub bajt typu null, znalezione przed bajtem przesunięcia *liczba* w *mbstr*.|

## <a name="remarks"></a>Uwagi

**_Mbsbtype —** funkcja określa typ bajtu w ciągu znaków wielobajtowych. Funkcja sprawdza tylko bajt przesunięcia *liczba* w *mbstr*, ignorując nieprawidłowe znaków przed określonym bajtem.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersja tej funkcji, bez **_l** sufiks używa bieżących ustawień regionalnych dla wszelkich zachowań; wersja, która **_l** sufiks jest identyczny, z tą różnicą, że korzysta z przekazanego parametru ustawień regionalnych w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Jeśli ciąg wejściowy jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca **_MBC_ILLEGAL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Dla stałych manifestu używanych jako wartości zwracane.

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
