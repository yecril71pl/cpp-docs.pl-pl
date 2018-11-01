---
title: _mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l
ms.date: 11/04/2016
apiname:
- _mbsnbicoll_l
- _mbsnbcoll_l
- _mbsnbcoll
- _mbsnbicoll
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
- mbsnbicoll
- mbsnbcoll
- mbsnbicoll_l
- _mbsnbcoll
- _mbsnbicoll
- _ftcsnicoll
- _ftcsncoll
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
- tcsncoll function
- tcsnicoll function
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
ms.openlocfilehash: c18faa3c93969a683b3ee3ef58dd02e1c1ae61f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665202"
---
# <a name="mbsnbcoll-mbsnbcolll-mbsnbicoll-mbsnbicolll"></a>_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l

Porównuje *n* bajtów dwa ciągi znaków wielobajtowych przy użyciu informacji o wielobajtowe strony kodowej.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ciągi znaków do porównania.

*Liczba*<br/>
Liczba bajtów do porównania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana określa relację z podciągów *ciąg1* i *ciąg2*.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*ciąg1* podciąg mniejszy niż *ciąg2* podciąg.|
|0|*ciąg1* podciąg identyczny z *ciąg2* podciąg.|
|> 0|*ciąg1* podciąg większy niż *ciąg2* podciąg.|

Jeśli *ciąg1* lub *ciąg2* jest **NULL** lub *liczba* jest większa niż **INT_MAX**, nieprawidłowy Procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **_NLSCMPERROR** i ustaw **errno** do **EINVAL**. Aby użyć **_NLSCMPERROR**, Włącz String.h lub Mbstring.h.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji porównuje, co najwyżej, pierwsze *liczba* bajtów w *ciąg1* i *ciąg2* i zwraca wartość wskazującą związek między wynikowy podciągi z *ciąg1* i *ciąg2*. Jeżeli bajt końcowy w podciągu *ciąg1* lub *ciąg2* jest bajtem wiodącym, nie jest objęty porównaniem; te funkcji porównują tylko całe znaki w podciągach. **_mbsnbicoll —** jest wersją uwzględniającą wielkości **_mbsnbcoll —**. Podobnie jak [_mbsnbcmp —](mbsnbcmp-mbsnbcmp-l.md) i [_mbsnbicmp —](mbsnbicmp-mbsnbicmp-l.md), **_mbsnbcoll —** i **_mbsnbicoll —** porównuje dwa ciągi znaków wielobajtowych według leksykograficznej kolejności określonej przez wielobajtową [strony kodowej](../../c-runtime-library/code-pages.md) aktualnie w użyciu.

Dla niektórych stron kodowych i odpowiednich zestawów znaków kolejności znaków w zestawie znaków mogą różnić się od kolejnością znaków leksykograficznych. W ustawieniach regionalnych "języka C", nie jest przypadek: kolejność znaków w zestawie znaków ASCII jest taka sama, jak w porządku leksykograficznym znaków. Jednak w niektórych stron kodowych Europejskich, na przykład znak "" (wartość 0x61) poprzedza znak "ź" (wartość 0xE4) znak ustawiane, ale znak "ź" poprzedza znak "" leksykograficznie. Aby wykonać leksykograficznych Porównanie ciągów według bajtów w wystąpieniu usługi, użyj **_mbsnbcoll —** zamiast **_mbsnbcmp —**; aby wyszukać tylko ciąg znaków równości, użyj **_mbsnbcmp —**.

Ponieważ **coll** funkcje zestawiają ciągi leksykograficznie dla celów porównawczych, natomiast **cmp** funkcje po prostu testują dla równości ciągu, **coll** funkcje znacznie wolniejsze niż odpowiadające **cmp** wersji. W związku z tym **coll** funkcje powinny być używane tylko wtedy, gdy istnieje różnica pomiędzy kolejnością zestawu znaków i kolejnością znaków leksykograficznych w bieżącej stronie kodowej, a różnica ta ma znaczenie dla porównania.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, bez **_l** sufiks używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersje **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych w zamian przekazanych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncoll —**|[_strncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll**|[_wcsncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsncoll_l**|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll_l —**|[_wcsncoll_l —](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsnicoll —**|[_strnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll —**|[_wcsnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|
|**_tcsnicoll_l**|[_strnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll_l —**|[_wcsnicoll_l —](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbcoll**|\<mbstring.h>|
|**_mbsnbcoll_l —**|\<mbstring.h>|
|**_mbsnbicoll —**|\<mbstring.h>|
|**_mbsnbicoll_l —**|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
