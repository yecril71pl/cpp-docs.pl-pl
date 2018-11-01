---
title: _mbccpy_s, _mbccpy_s_l
ms.date: 11/04/2016
apiname:
- _mbccpy_s
- _mbccpy_s_l
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
- _mbccpy_s_l
- mbccpy_s_l
- mbccpy_s
- _mbccpy_s
helpviewer_keywords:
- tccpy_s_l function
- _tccpy_s function
- _mbccpy_s function
- mbccpy_s function
- tccpy_s function
- mbccpy_s_l function
- _tccpy_s_l function
- _mbccpy_s_l function
ms.assetid: b6e965fa-53c1-4ec3-85ef-a1c4b4f2b2da
ms.openlocfilehash: f9a7554630bd3b46196358c01c21b99978c53e53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575064"
---
# <a name="mbccpys-mbccpysl"></a>_mbccpy_s, _mbccpy_s_l

Kopiuje jeden znak wielobajtowy z ciągu do innego ciągu. Te wersje [_mbccpy —, _mbccpy_l —](mbccpy-mbccpy-l.md) mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
errno_t _mbccpy_s(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src
);
errno_t _mbccpy_s_l(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src,
   locale_t locale
);
template <size_t size>
errno_t _mbccpy_s(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbccpy_s_l(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src,
   locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*dest*<br/>
Miejsce docelowe kopii.

*buffSizeInBytes*<br/>
Rozmiar buforu miejsca docelowego.

*pCopied*<br/>
Wypełniony liczbą bajtów skopiowanych (1 lub 2, jeśli kończy się pomyślnie). Przekaż **NULL** Jeśli nie dba o numerze.

*src*<br/>
Znak wielobajtowy do skopiowania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie; Kod błędu. Jeśli *src* lub *dest* jest **NULL**, lub jeśli są większe niż **buffSizeinBytes** bajtów zostałoby skopiowanych do *dest*, a następnie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **EINVAL** i **errno** ustawiono **EINVAL**.

## <a name="remarks"></a>Uwagi

**_Mbccpy_s —** funkcja kopiuje jeden znak wielobajtowy z *src* do *dest*. Jeśli *src* nie wskazuje bajtu wiodącego znaku wielobajtowego jak ustalono przez wywołanie niejawne [_ismbblead](ismbblead-ismbblead-l.md), wówczas bajt pojedynczy, *src* punkty są kopiowane. Jeśli *src* wskazuje na bajt wiodący, ale następny bajt jest 0, a więc jest nieważny, wówczas 0 jest kopiowane do *dest*, **errno** ustawiono **EILSEQ**i funkcja zwraca **EILSEQ**.

**_mbccpy_s —** nie dołącza terminatora null; Jednakże, jeśli *src* wskazuje znak null, a następnie tego null jest kopiowany do *dest* (jest to po prostu regularnie kopia jednobajtowa).

Wartość w *pCopied* jest wypełniona liczbą bajtów skopiowanych. Możliwe wartości to 1 i 2, jeśli operacja się powiedzie. Jeśli **NULL** jest przekazywana, ten parametr jest ignorowany.

|*src*|skopiowane do *miejsca docelowego*|*pCopied*|Wartość zwracana|
|-----------|----------------------|---------------|------------------|
|inne niż bajt wiodący|inne niż bajt wiodący|1|0|
|0|0|1|0|
|bajt wiodący, następnie inne niż 0|bajt wiodący, następnie inne niż 0|2|0|
|bajt wiodący, następnie 0|0|1|**EILSEQ**|

Należy pamiętać, że drugi wiersz jest szczególnym przypadkiem pierwszego. Należy także zauważyć, że tabela zakłada *buffSizeInBytes* >= *pCopied*.

**_mbccpy_s —** używa bieżących ustawień regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych. **_mbccpy_s_l —** jest taka sama jak **_mbccpy_s —** z tą różnicą, że **_mbccpy_s_l —** korzysta z regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s —**|Mapy i makro lub funkcji śródwierszowej.|**_mbccpy_s**|Mapy i makro lub funkcji śródwierszowej.|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
