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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 85db4e478b070823bb14028018d918e0f3cabbd7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920321"
---
# <a name="_mbccpy_s-_mbccpy_s_l"></a>_mbccpy_s, _mbccpy_s_l

Kopiuje jeden znak wielobajtowy z ciągu do innego ciągu. Te wersje [_mbccpy _mbccpy_l](mbccpy-mbccpy-l.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Kopiuj miejsce docelowe.

*buffSizeInBytes*<br/>
Rozmiar buforu docelowego.

*pCopied*<br/>
Wypełniono z liczbą skopiowanych bajtów (1 lub 2, jeśli powodzenie). Przekaż **wartość null** , jeśli nie masz opieki dotyczącej liczby.

*src*<br/>
Znak wielobajtowy do skopiowania.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli pomyślne; kod błędu w przypadku niepowodzenia. Jeśli *src* lub *docelowy* ma **wartość null**lub jeśli więcej niż **buffSizeinBytes** bajtów zostałyby skopiowane do miejsca *docelowego*, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcje zwracają **EINVAL** i **errno** są ustawione na **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_mbccpy_s** kopiuje jeden znak wielobajtowy z *src* do miejsca *docelowego*. Jeśli *src* nie wskazuje bajtu wiodącego znaku wielobajtowego, który jest określony przez niejawne wywołanie [_ismbblead](ismbblead-ismbblead-l.md), to pojedynczy bajt, do którego wskazuje element *src* , jest kopiowany. Jeśli *src* wskazuje na bajt wiodący, ale następujący bajt ma wartość 0, a w ten sposób jest nieprawidłowy, wartość 0 jest kopiowana do miejsca *docelowego*, **errno** jest ustawiona na **EILSEQ**, a funkcja zwraca **EILSEQ**.

**_mbccpy_s** nie dołącza terminatora null; Jeśli jednak element *src* wskazuje znak null, wówczas wartość null jest kopiowana do miejsca *docelowego* (jest to tylko zwykła kopia jednobajtowa).

Wartość w *pCopied* jest wypełniana liczbą bajtów skopiowanych. Możliwe wartości to 1 i 2, jeśli operacja zakończyła się pomyślnie. Jeśli **wartość null** jest przenoszona, ten parametr jest ignorowany.

|*src*|Skopiowano do miejsca *docelowego*|*pCopied*|Wartość zwracana|
|-----------|----------------------|---------------|------------------|
|bajty niebędące liderem|bajty niebędące liderem|1|0|
|0|0|1|0|
|bajt wiodący, po którym następuje wartość niezerowa|bajt wiodący, po którym następuje wartość niezerowa|2|0|
|bajt wiodący, po którym następuje 0|0|1|**EILSEQ**|

Należy zauważyć, że drugi wiersz jest tylko szczególnym przypadkiem pierwszego. Należy również pamiętać, że tabela przyjmuje *buffSizeInBytes* >= *pCopied*.

**_mbccpy_s** używa bieżących ustawień regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych. **_mbccpy_s_l** jest taka sama jak **_mbccpy_s** , z tą różnicą, że **_mbccpy_s_l** korzysta z ustawień regionalnych przewidzianych dla wszelkich zachowań zależnych od ustawień regionalnych.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|Mapuje na makro lub funkcję wbudowaną.|**_mbccpy_s**|Mapuje na makro lub funkcję wbudowaną.|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring. h>|
|**_mbccpy_s_l**|\<mbstring. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Ustawienie](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
