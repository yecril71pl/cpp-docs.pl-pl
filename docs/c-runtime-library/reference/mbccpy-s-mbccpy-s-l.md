---
title: _mbccpy_s, _mbccpy_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a3a52314209b62c818623e315757dcd358ec491
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404031"
---
# <a name="mbccpys-mbccpysl"></a>_mbccpy_s, _mbccpy_s_l

Kopiuje jeden znaków wielobajtowych z ciągu na inny ciąg. Te wersje programu [_mbccpy —, _mbccpy_l —](mbccpy-mbccpy-l.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Lokalizacji docelowej kopiowania.

*buffSizeInBytes*<br/>
Rozmiar buforu docelowego.

*pCopied*<br/>
Wypełniony liczbę bajtów skopiowanych (1 lub 2 w przypadku powodzenia). Przekaż **NULL** Jeśli nie interesują o numerze.

*src*<br/>
Znaków wielobajtowych do skopiowania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero w przypadku powodzenia; błąd o kodzie błędu. Jeśli *src* lub *dest* jest **NULL**, lub jeśli więcej niż **buffSizeinBytes** bajtów jest kopiowany do *dest*, następnie program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcje zwracają **einval —** i **errno** ustawiono **einval —**.

## <a name="remarks"></a>Uwagi

**_Mbccpy_s —** funkcja kopiuje znaków wielobajtowych jednego z *src* do *dest*. Jeśli *src* nie wskazuje bajtu znaków wielobajtowych określone przez wywołanie niejawne [_ismbblead —](ismbblead-ismbblead-l.md), następnie jednobajtowych który *src* jest kopiowany punkty. Jeśli *src* punktów bajtu, ale następny bajt jest 0 i w związku z tym nieprawidłowe, a następnie 0 jest kopiowany do *dest*, **errno** ustawiono **eilseq —** i funkcja zwraca **eilseq —**.

**_mbccpy_s —** nie dołączał terminatorem null, ale jeśli *src* wskazuje znak null, a następnie tej wartości null jest kopiowany do *dest* (jest to po prostu regularnych kopii jednobajtowe).

Wartość w *pCopied* jest wypełniony liczba bajtów skopiowane. Możliwe wartości to 1 i 2, jeśli operacja zakończy się pomyślnie. Jeśli **NULL** jest przekazywana, ten parametr jest ignorowany.

|*src*|skopiowane do *docelowy*|*pCopied*|Wartość zwracana|
|-----------|----------------------|---------------|------------------|
|z systemem innym niż — bajtu|z systemem innym niż — bajtu|1|0|
|0|0|1|0|
|bajtu następuje z systemem innym niż 0|bajtu następuje z systemem innym niż 0|2|0|
|bajtu następuje 0|0|1|**EILSEQ —**|

Należy pamiętać, że drugi wiersz po prostu szczególnych przypadkach pierwszy. Należy także zauważyć, który przyjmuje tabeli *buffSizeInBytes* >= *pCopied*.

**_mbccpy_s —** używa bieżące ustawienia regionalne dla dowolnego zachowanie zależnych od ustawień regionalnych. **_mbccpy_s_l —** jest taka sama jak **_mbccpy_s —** z tą różnicą, że **_mbccpy_s_l —** korzysta z ustawień regionalnych przekazano wszystkie działania zależne od ustawień regionalnych.

W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można wnioskować o długości buforu automatycznie, co eliminuje konieczność określić argument rozmiar. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s —**|Map — makro lub wewnętrznej funkcji.|**_mbccpy_s**|Map — makro lub wewnętrznej funkcji.|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
