---
title: _mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l
ms.date: 11/04/2016
apiname:
- _mbcjistojms
- _mbcjmstojis
- _mbcjistojms_l
- _mbcjmstojis_l
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
ms.openlocfilehash: 22cf8eeb5f99b6abee624aa3b1d06246d7230652
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156827"
---
# <a name="mbcjistojms-mbcjistojmsl-mbcjmstojis-mbcjmstojisl"></a>_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l

Konwertuje między znakami Japan Industry Standard (JIS) i Japonia, część firmy Microsoft (JMS).

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*c*<br/>
Znak do przekształcenia.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

W japońskich ustawieniach regionalnych funkcje te przywracają przekonwertowany znak lub zwracają 0, jeśli konwersja nie jest możliwa. W ustawieniach regionalnych innych niż japońska funkcje te zwracają znaku przekazany.

## <a name="remarks"></a>Uwagi

**_Mbcjistojms —** funkcja konwertuje znak Japan Industry Standard (JIS) na znaki Kanji Microsoft (Shift JIS). Znak jest konwertowany tylko wtedy, gdy potencjalny klienta i szlak bajtów są w zakresie 0x21 — 0x7E. Jeśli potencjalny klient bajt wiodący lub próbny jest poza tym zakresem **errno** ustawiono **EILSEQ**. Aby uzyskać więcej informacji na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**_Mbcjmstojis —** funkcja konwertuje znak Shift JIS znak JIS. Znak jest konwertowany tylko wtedy, gdy bajt jest w zakresie 0x81-0x9F lub wartość 0xE0 — 0xFC i bajt jest w zasięgu 0x40-0x7E lub 0x80 - 0xFC. Należy pamiętać, że niektóre punkty kodów w tym zakresu nie mają postaci przypisanej, a zatem nie może zostać przekonwertowany.

Wartość *c* powinna być wartością 16-bitową, której górne 8 bitów reprezentuje bajt wiodący znaku do konwersji i której dolne 8 bitów reprezentuje bajt.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, bez **_l** sufiks używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersje **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych w zamian przekazanych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

We wcześniejszych wersjach **_mbcjistojms —** i **_mbcjmstojis —** były nazywane **jistojms** i **jmstojis**, odpowiednio. **_mbcjistojms —**, **_mbcjistojms_l —**, **_mbcjmstojis —** i **_mbcjmstojis_l —** powinny być używane zamiast tego.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbcjistojms**|\<mbstring.h>|
|**_mbcjistojms_l**|\<mbstring.h>|
|**_mbcjmstojis**|\<mbstring.h>|
|**_mbcjmstojis_l**|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
