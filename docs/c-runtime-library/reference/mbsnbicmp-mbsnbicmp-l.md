---
title: _mbsnbicmp, _mbsnbicmp_l
ms.date: 4/2/2020
api_name:
- _mbsnbicmp_l
- _mbsnbicmp
- _o__mbsnbicmp
- _o__mbsnbicmp_l
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
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _mbsnbicmp_l
helpviewer_keywords:
- _tcsnicmp_l function
- _strnicmp function
- mbsnbicmp_l function
- _wcsnicmp_l function
- _mbsnbicmp function
- _mbsnbicmp_l function
- _tcsnicmp function
- _strnicmp_l function
- mbsnbicmp function
- _wcsnicmp function
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
ms.openlocfilehash: 80d2708396cdaeb86c25932c3d13129fb318719a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340578"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp, _mbsnbicmp_l

Porównuje **n** bajtów dwóch ciągów znaków wielobajtowych i ignoruje przypadek.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _mbsnbicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*ciąg1*, *ciąg2*<br/>
Ciągi zakończone wartością null do porównania.

*Liczba*<br/>
Liczba bajtów do porównania.

## <a name="return-value"></a>Wartość zwracana

Zwracana wartość wskazuje relację między podciągami.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*podciąg 1* podciąg mniejszy niż podciąg *string2.*|
|0|*podciąg string1* identyczny z podciągiem *string2.*|
|> 0|*podciąg 1* ciąg większy niż podciąg *string2.*|

W razie błędu **_mbsnbicmp** zwraca **_NLSCMPERROR**, który jest zdefiniowany w String.h i Mbstring.h.

## <a name="remarks"></a>Uwagi

Funkcja **_mbsnbicmp** wykonuje porównanie porządkowe co najwyżej pierwszy *bajtów liczby* *ciągów1* i *string2*. Porównanie odbywa się przez konwersję każdego znaku na małe litery; [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) jest wersją **_mbsnbicmp**uwzględniającą wielkość liter . Porównanie kończy się, jeśli kończący się znak null zostanie osiągnięty w obu ciągach przed porównaniem znaków *zliczania.* Jeśli ciągi są równe, gdy kończący się znak null zostanie osiągnięty w obu ciągów przed *zliczanie* znaków są porównywane, krótszy ciąg jest mniejszy.

**_mbsnbicmp** jest podobny do [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md), z tą różnicą, że porównuje ciągi do *zliczania* bajtów zamiast według znaków.

Dwa ciągi zawierające znaki znajdujące się między 'Z' i 'a' w\\tabeli ASCII ('[', '\`', ']', '^', '_', i ' ') porównują się inaczej, w zależności od ich przypadku. Na przykład dwa ciągi "ABCDE" i "ABCD^" porównują jeden ze sposobów, jeśli porównanie jest małe ("abcde" > "abcd^") i w drugą stronę ("ABCDE" < "ABCD^"), jeśli jest to wielkie litery.

**_mbsnbicmp** rozpoznaje sekwencje znaków wielobajtowych zgodnie z aktualnie używaną [stroną kodową wielobajtową.](../../c-runtime-library/code-pages.md) Nie ma na to wpływu bieżące ustawienie ustawień regionalnych.

Jeśli *ciąg1* lub *ciąg2* jest wskaźnikiem zerowym, **_mbsnbicmp** wywołuje nieprawidłowy program obsługi parametrów zgodnie z opisem w [programie Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcja zwraca **_NLSCMPERROR** i ustawia **errno** na **EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md).

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
