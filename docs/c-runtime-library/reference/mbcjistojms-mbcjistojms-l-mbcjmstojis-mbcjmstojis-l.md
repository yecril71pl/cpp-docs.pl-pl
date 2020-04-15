---
title: _mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l
ms.date: 4/2/2020
api_name:
- _mbcjistojms
- _mbcjmstojis
- _mbcjistojms_l
- _mbcjmstojis_l
- _o__mbcjistojms
- _o__mbcjistojms_l
- _o__mbcjmstojis
- _o__mbcjmstojis_l
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
- mbcjistojms
- _mbcjistojms
- _mbcjistojms_l
- _mbcjmstojis_l
- _mbcjmstojis
- mbcjmstojis_l
- mbcjistojms_l
- mbcjmstojis
helpviewer_keywords:
- _mbcjmstojis_l function
- _mbcjistojms function
- mbcjmstojis function
- _mbcjistojms_l function
- _mbcjmstojis function
- mbcjistojms function
- mbcjmstojis_l function
- mbcjistojms_l function
ms.assetid: dece5127-b337-40a4-aa10-53320a2c9432
ms.openlocfilehash: ef0010088543f1c580e536f120cae681a7582491
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341181"
---
# <a name="_mbcjistojms-_mbcjistojms_l-_mbcjmstojis-_mbcjmstojis_l"></a>_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l

Konwertuje między znakami Japan Industry Standard (JIS) i Japan Microsoft (JMS).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
unsigned int _mbcjistojms(
   unsigned int c
);
unsigned int _mbcjistojms_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbcjmstojis(
   unsigned int c
);
unsigned int _mbcjmstojis_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*C*<br/>
Znak do konwersji.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

W japońskich ustawieniach regionalnych te funkcje zwracają przekonwertowany znak lub zwracają 0, jeśli konwersja nie jest możliwa. W ustawieniach regionalnych innych niż japońskie te funkcje zwracają znak przekazany.

## <a name="remarks"></a>Uwagi

Funkcja **_mbcjistojms** konwertuje znak Japońskiego Standardu Przemysłowego (JIS) na znak Microsoft Kanji (Shift JIS). Znak jest konwertowany tylko wtedy, gdy bajty potencjalnego klienta i szlaku znajdują się w zakresie 0x21 - 0x7E. Jeśli bajt wiodący lub próbny znajduje się poza tym zakresem, **errno** jest ustawiony na **EILSEQ**. Aby uzyskać więcej informacji na temat tego i innych kodów błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Funkcja **_mbcjmstojis** konwertuje znak Shift JIS na znak JIS. Znak jest konwertowany tylko wtedy, gdy bajt potencjalnego klienta znajduje się w zakresie 0x81 - 0x9F lub 0xE0 - 0xFC, a bajt szlaku znajduje się w zakresie 0x40 - 0x7E lub 0x80 - 0xFC. Należy zauważyć, że niektóre punkty kodu w tym zakresie nie mają przypisanego znaku i dlatego nie można ich przekonwertować.

Wartość *c* powinna być wartością 16-bitową, której górne 8 bitów reprezentuje bajt wiodący znaku do konwersji i których dolne 8 bitów reprezentuje bajt szlaku.

Na wartość wyjściową ma wpływ ustawienie **LC_CTYPE** kategorii ustawień regionalnych; zobacz [setlocale,](setlocale-wsetlocale.md) aby uzyskać więcej informacji. Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; wersje z sufiksem **_l** są identyczne, z tą różnicą, że zamiast tego używają parametru ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

We wcześniejszych wersjach **_mbcjistojms** i **_mbcjmstojis** nazywano odpowiednio **jistojms** i **jmstojis.** **_mbcjistojms zamiast**tego należy stosować **_mbcjmstojis**i **_mbcjmstojis_l** **_mbcjistojms_l.**

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbcjistojms**|\<mbstring.h>|
|**_mbcjistojms_l**|\<mbstring.h>|
|**_mbcjmstojis**|\<mbstring.h>|
|**_mbcjmstojis_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
