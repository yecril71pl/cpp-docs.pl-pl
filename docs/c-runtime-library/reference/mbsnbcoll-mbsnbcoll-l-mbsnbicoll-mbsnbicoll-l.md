---
title: _mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l
ms.date: 4/2/2020
api_name:
- _mbsnbicoll_l
- _mbsnbcoll_l
- _mbsnbcoll
- _mbsnbicoll
- _o__mbsnbcoll
- _o__mbsnbcoll_l
- _o__mbsnbicoll
- _o__mbsnbicoll_l
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
- _mbsnbcoll
- _mbsnbcoll_l
- _mbsnbicoll
- mbsnbcoll_l
helpviewer_keywords:
- _mbsnbcoll_l function
- mbsnbcoll_l function
- _mbsnbcoll function
- _tcsnicoll function
- mbsnbcoll function
- mbsnbicoll_l function
- mbsnbicoll function
- _tcsncoll function
- _mbsnbicoll function
- _mbsnbicoll_l function
- _tcsncoll_l function
- _tcsnicoll_l function
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
ms.openlocfilehash: 0b02a34f9b721e4cfcf07ac3679d0dce166a4ff7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340741"
---
# <a name="_mbsnbcoll-_mbsnbcoll_l-_mbsnbicoll-_mbsnbicoll_l"></a>_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l

Porównuje *n* bajtów dwóch ciągów znaków wielobajtowych przy użyciu informacji o wielobajtowej stronie kodowej.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _mbsnbcoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbcoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
int _mbsnbicoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*ciąg1*, *ciąg2*<br/>
Ciągi do porównania.

*Liczba*<br/>
Liczba bajtów do porównania.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwracana wartość wskazuje relację podciągów *string1* i *string2*.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*podciąg 1* podciąg mniejszy niż podciąg *string2.*|
|0|*podciąg string1* identyczny z podciągiem *string2.*|
|> 0|*podciąg 1* ciąg większy niż podciąg *string2.*|

Jeśli *ciąg1* lub *ciąg2* ma **wartość NULL** lub *liczba* jest większa niż **INT_MAX,** wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [programie Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcje te zwracają **_NLSCMPERROR** i ustawić **errno** na **EINVAL**. Aby użyć **_NLSCMPERROR**, należy dołączyć string.h lub Mbstring.h.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji zestawia co najwyżej pierwsze *bajty zliczania* w *ciągu1* i *string2* i zwraca wartość wskazującą relację między wynikowymi podciągami *string1* i *string2*. Jeśli końcowy bajt w podciągach *string1* lub *string2* jest bajtem wiodącym, nie jest uwzględniony w porównaniu; te funkcje porównują tylko pełne znaki w podciągach. **_mbsnbicoll** jest wersją **_mbsnbcoll**niewrażliwą na przypadek . Podobnie jak [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) i [_mbsnbicmp,](mbsnbicmp-mbsnbicmp-l.md) **_mbsnbcoll** i **_mbsnbicoll** zestawiają dwa ciągi znaków wielobajtowych zgodnie z kolejnością leksykograficzną określoną przez aktualnie używaną [stronę kodową](../../c-runtime-library/code-pages.md) multibajtów.

W przypadku niektórych stron kodowych i odpowiadających im zestawów znaków kolejność znaków w zestawie znaków może różnić się od kolejności znaków leksykograficznych. W ustawieniach regionalnych "C" tak nie jest: kolejność znaków w zestawie znaków ASCII jest taka sama jak kolejność leksykograficzna znaków. Jednak na niektórych europejskich stronach kodowych, na przykład, znak "a" (wartość 0x61) poprzedza znak "ä" (wartość 0xE4) w zestawie znaków, ale znak "ä" poprzedza znak "a" leksykograficznie. Aby wykonać leksykograficzne porównanie ciągów według bajtów w takim wystąpieniu, należy użyć **_mbsnbcoll,** a nie **_mbsnbcmp;** aby sprawdzić tylko, czy nie ma równości ciągów, użyj **_mbsnbcmp**.

Ponieważ **coll** funkcje zestawiają ciągi leksykograficznie do porównania, podczas gdy funkcje **cmp** po prostu testują równość ciągów, funkcje **coll** są znacznie wolniejsze niż odpowiednie wersje **cmp.** W związku z tym funkcje **coll** powinny być używane tylko wtedy, gdy istnieje różnica między kolejnością zestawu znaków i kolejności znaków leksykograficznych na bieżącej stronie kodowej i ta różnica jest interesująca dla porównania.

Na wartość wyjściową ma wpływ ustawienie **LC_CTYPE** kategorii ustawień regionalnych; zobacz [setlocale,](setlocale-wsetlocale.md) aby uzyskać więcej informacji. Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; wersje z sufiksem **_l** są identyczne, z tą różnicą, że zamiast tego używają parametru ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncoll**|[_strncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll**|[_wcsncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsncoll_l**|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll_l**|[_wcsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsnicoll**|[_strnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll**|[_wcsnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|
|**_tcsnicoll_l**|[_strnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll_l**|[_wcsnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbcoll**|\<mbstring.h>|
|**_mbsnbcoll_l**|\<mbstring.h>|
|**_mbsnbicoll**|\<mbstring.h>|
|**_mbsnbicoll_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcoll — Funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
