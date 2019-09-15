---
title: _mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l
ms.date: 11/04/2016
api_name:
- _mbcjistojms
- _mbcjmstojis
- _mbcjistojms_l
- _mbcjmstojis_l
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
ms.openlocfilehash: 6bf1109cfba93042bd00acde4812706c1bbf7a01
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952587"
---
# <a name="_mbcjistojms-_mbcjistojms_l-_mbcjmstojis-_mbcjmstojis_l"></a>_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l

Konwertuje znaki w języku Japonia Industry Standard (JIS) i Japonia Microsoft (JMS).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Znak do przekonwertowania.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

W przypadku japońskich ustawień regionalnych te funkcje zwracają przekonwertowany znak lub zwraca wartość 0, jeśli konwersja nie jest możliwa. W przypadku ustawień regionalnych innych niż japońskie funkcje te zwracają znak przesłany.

## <a name="remarks"></a>Uwagi

Funkcja **_mbcjistojms** konwertuje znak w języku Japonia Industry Standard (JIS) na znak Microsoft kanji (Shift JIS). Znak jest konwertowany tylko wtedy, gdy bajty wiodące i końcowe znajdują się w zakresie 0x21-0x7E. Jeśli bajt potencjalnego klienta lub wersji próbnej znajduje się poza tym zakresem, **errno** jest ustawiona na **EILSEQ**. Aby uzyskać więcej informacji na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Funkcja **_mbcjmstojis** konwertuje znak Shift JIS na znak JIS. Znak jest konwertowany tylko wtedy, gdy bajt wiodący znajduje się w zakresie 0x81-0x9F lub wartość 0xE0-0xFC, a bajt końcowy znajduje się w zakresie 0x40-0x7E lub 0x80-0xFC. Należy zauważyć, że niektóre punkty kodu w tym zakresie nie mają przypisanego znaku i dlatego nie mogą być konwertowane.

Wartość *c* powinna być wartością 16-bitową, której górne 8 bitów reprezentuje bajt wiodący znaku do przekonwertowania i którego Dolna część 8 bitów reprezentuje bajt końcowy.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** kategorii ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocals](setlocale-wsetlocale.md) . Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. wersje z sufiksem **_l** są identyczne, z tą różnicą, że w zamian korzystają z przekazaną parametrem ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

We wcześniejszych wersjach **_mbcjistojms** i **_mbcjmstojis** były odpowiednio nazywane **jistojms** i **jmstojis**. Zamiast tego należy użyć **_mbcjistojms**, **_mbcjistojms_l**, **_mbcjmstojis** i **_mbcjmstojis_l** .

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbcjistojms**|\<mbstring.h>|
|**_mbcjistojms_l**|\<mbstring.h>|
|**_mbcjmstojis**|\<mbstring.h>|
|**_mbcjmstojis_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
