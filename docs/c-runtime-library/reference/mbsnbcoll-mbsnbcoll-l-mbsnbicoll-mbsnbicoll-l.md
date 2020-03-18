---
title: _mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l
ms.date: 11/04/2016
api_name:
- _mbsnbicoll_l
- _mbsnbcoll_l
- _mbsnbcoll
- _mbsnbicoll
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
ms.openlocfilehash: d759bda0133a95406a586011d39d69074283bf97
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438209"
---
# <a name="_mbsnbcoll-_mbsnbcoll_l-_mbsnbicoll-_mbsnbicoll_l"></a>_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l

Porównuje *n* bajtów dwóch ciągów znaków wielobajtowych przy użyciu wielobajtowych informacji o stronie kodowej.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*count*<br/>
Liczba bajtów do porównania.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana określa relację podciągów wartości *ciąg1* i *ciąg2*.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*ciąg1* podciągu krótszy niż *ciąg2* podciąg.|
|0|*ciąg1* podciąg identyczny z podciągiem *ciąg2* .|
|> 0|*ciąg1* podciąg jest większy niż *ciąg2* podciąg.|

Jeśli *ciąg1* lub *ciąg2* ma **wartość null** lub *Liczba* jest większa niż **INT_MAX**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **_NLSCMPERROR** i ustawiają **errno** na **EINVAL**. Aby użyć **_NLSCMPERROR**, Uwzględnij ciąg. h lub mbstring. h.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji sortuje, najwyżej *, pierwsze* bajty w parametrach *ciąg1* i *ciąg2* i zwraca wartość wskazującą zależność między wynikowymi podciągami wartości *ciąg1* i *ciąg2*. Jeśli końcowy bajt w podciągu *ciąg1* lub *ciąg2* jest bajtem wiodącym, nie jest uwzględniany w porównaniu; te funkcje porównują tylko kompletne znaki w podciągach. **_mbsnbicoll** to wersja **_mbsnbcoll**niezależna od wielkości liter. Podobnie jak [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) i [_mbsnbicmp](mbsnbicmp-mbsnbicmp-l.md), **_mbsnbcoll** i **_mbsnbicoll** sortują dwa ciągi znaków wielobajtowych zgodnie z kolejnością leksykograficznych określoną przez obecnie używaną [stronę kodową](../../c-runtime-library/code-pages.md) wielobajtowego.

W przypadku niektórych stron kodowych i odpowiednich zestawów znaków kolejność znaków w zestawie znaków może różnić się od kolejności znaków leksykograficznych. W ustawieniach regionalnych języka C nie jest to przypadek: kolejność znaków w zestawie znaków ASCII jest taka sama jak kolejność leksykograficznych znaków. Jednak w niektórych europejskich stronach kodowych, na przykład, znak "a" (wartość 0x61) poprzedza znak "ä" (wartość 0xE4) w zestawie znaków, ale znak "ä" poprzedza znak "a" lexicographically. Aby wykonać leksykograficznych porównanie ciągów przez bajty w takich przypadkach, użyj **_mbsnbcoll** , a nie **_mbsnbcmp**; Aby sprawdzić tylko dla równości ciągów, użyj **_mbsnbcmp**.

Ponieważ funkcje **Coll** sortują ciągi lexicographically do porównania, podczas gdy funkcje **CMP** po prostu testują równość ciągów, funkcje **Coll** są znacznie wolniejsze niż odpowiednie wersje programu **CMP** . W związku z tym, funkcje **Coll** powinny być używane tylko wtedy, gdy istnieje różnica pomiędzy kolejnością zestawu znaków i kolejnością znaków leksykograficznych na bieżącej stronie kodowej, a różnica jest istotna dla porównania.

Wartość wyjściowa jest zależna od ustawienia ustawienia kategorii **LC_CTYPE** ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocals](setlocale-wsetlocale.md) . Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. wersje z sufiksem **_l** są identyczne, z tą różnicą, że korzystają z przekazaną w zamian parametru ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

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
|**_mbsnbcoll**|\<mbstring. h >|
|**_mbsnbcoll_l**|\<mbstring. h >|
|**_mbsnbicoll**|\<mbstring. h >|
|**_mbsnbicoll_l**|\<mbstring. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
