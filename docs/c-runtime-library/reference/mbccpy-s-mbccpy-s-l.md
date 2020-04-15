---
title: _mbccpy_s, _mbccpy_s_l
ms.date: 4/2/2020
api_name:
- _mbccpy_s
- _mbccpy_s_l
- _o__mbccpy_s
- _o__mbccpy_s_l
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
ms.openlocfilehash: 08df395c6978c84b3f53ed0b07ce988afd0249f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341231"
---
# <a name="_mbccpy_s-_mbccpy_s_l"></a>_mbccpy_s, _mbccpy_s_l

Kopiuje jeden znak wielobajtowy z ciągu do innego ciągu. Te wersje [_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Dest*<br/>
Skopiuj miejsce docelowe.

*buffSizeInBytes buffSizeInBytes buffSizeInBytes BuffS*<br/>
Rozmiar buforu docelowego.

*pcopied*<br/>
Wypełniona liczbą skopiowanych bajtów (1 lub 2, jeśli się powiedzie). Przekaż **wartość NULL,** jeśli nie zależy Ci na numerze.

*src*<br/>
Znak wielobajtowy do skopiowania.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie; kod błędu w przypadku awarii. Jeśli *src* lub *dest* ma **wartość NULL**lub jeśli więcej niż **buffSizeinBytes** bajtów zostanie skopiowany do *dest*, a następnie nieprawidłowy program obsługi parametrów jest wywoływana, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, funkcje zwracają **EINVAL** i **errno** jest ustawiona na **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_mbccpy_s** kopiuje jeden znak wielobajtowy z *src* do *dest*. Jeśli *src* nie wskazuje na bajt wiodący znaku wielobajtowego, jak określa niejawne wywołanie [_ismbblead](ismbblead-ismbblead-l.md), wówczas pojedynczy bajt, który *wskazuje src* jest kopiowany. Jeśli *src* wskazuje na bajt wiodący, ale następujący bajt jest 0 i w związku z tym nieprawidłowy, następnie 0 jest kopiowany do *dest*, **errno** jest ustawiona na **EILSEQ**, a funkcja zwraca **EILSEQ**.

**_mbccpy_s** nie dołącza terminatora zerowego; jednak jeśli *src* wskazuje znak null, to ta wartość null jest kopiowana do *dest* (jest to tylko zwykła kopia jedno bajtowa).

Wartość w *skopiowanym pcopied* jest wypełniona liczbą skopiowanych bajtów. Możliwe wartości to 1 i 2, jeśli operacja zakończy się pomyślnie. Jeśli **null** jest przekazywana, ten parametr jest ignorowany.

|*src*|skopiowane do *dest*|*pcopied*|Wartość zwracana|
|-----------|----------------------|---------------|------------------|
|nie-ołowiu bajt|nie-ołowiu bajt|1|0|
|0|0|1|0|
|lead-byte, po którym następuje|lead-byte, po którym następuje|2|0|
|lead-byte, a następnie 0|0|1|**OKRĘG WYBORCZY EILSEQ**|

Należy zauważyć, że drugi wiersz jest tylko szczególnym przypadkiem pierwszego. Należy również zauważyć, że tabela zakłada *buffSizeInBytes* >= *pCopied*.

**_mbccpy_s** używa bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych. **_mbccpy_s_l** jest identyczna **z _mbccpy_s** z tą różnicą, że **_mbccpy_s_l** używa ustawień regionalnych przekazanych dla zachowania zależnego od ustawień regionalnych.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|Mapuje do funkcji makro lub wbudowanej.|**_mbccpy_s**|Mapuje do funkcji makro lub wbudowanej.|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
