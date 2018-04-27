---
title: _mbsnbcoll —, _mbsnbcoll_l —, _mbsnbicoll —, _mbsnbicoll_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5be9c6cb3421b5ba1b191977f70a35d7ffc38625
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="mbsnbcoll-mbsnbcolll-mbsnbicoll-mbsnbicolll"></a>_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l

Porównuje *n* bajtów dwa ciągi znaków wielobajtowych przy użyciu informacji wielobajtowe stronę kodową.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Wartości zwracanej wskazuje relacja podciągów *ciąg1* i *ciąg2*.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*ciąg1* podciąg mniej niż *ciąg2* podciąg.|
|0|*ciąg1* podciąg taki sam jak *ciąg2* podciąg.|
|> 0|*ciąg1* podciąg większe *ciąg2* podciąg.|

Jeśli *ciąg1* lub *ciąg2* jest **NULL** lub *liczba* jest większa niż **int_max —**, nieprawidłowego Parametr program obsługi zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają **_NLSCMPERROR** i ustaw **errno** do **einval —**. Aby użyć **_NLSCMPERROR**, to String.h lub Mbstring.h.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji posortuje, co najwyżej pierwszy *liczba* bajtów w *ciąg1* i *ciąg2* i zwraca wartość wskazującą relacji między powstałe w ten sposób podciągi z *ciąg1* i *ciąg2*. Jeśli końcowego bajtów w podciąg *ciąg1* lub *ciąg2* jest bajtu, nie znajduje się w porównaniu; tylko pełną znaków podciągów porównanie tych funkcji. **_mbsnbicoll —** jest rozróżniana wielkość liter wersja **_mbsnbcoll —**. Podobnie jak [_mbsnbcmp —](mbsnbcmp-mbsnbcmp-l.md) i [_mbsnbicmp —](mbsnbicmp-mbsnbicmp-l.md), **_mbsnbcoll —** i **_mbsnbicoll —** porównuje dwa ciągi znaków wielobajtowych zgodnie z lexicographic kolejności określonej przez wielobajtowe [strona kodowa](../../c-runtime-library/code-pages.md) obecnie w użyciu.

Dla niektórych stron kodowych i odpowiednich zestawów znaków kolejność znaków w zestawie znaków mogą różnić się od kolejność lexicographic znaków. Zgodnie z ustawieniami regionalnymi "C", nie jest to to: kolejność znaków w zestawie znaków ASCII, jest taka sama jak lexicographic kolejność znaków. Jednak w niektórych stron kodowych Europejskich, na przykład znak "" (wartość 0x61) poprzedzające znak "ź" (0xE4) znaków wartość, ale znak "ź" poprzedza znak "" lexicographically. Aby wykonać lexicographic porównania ciągów przy bajtów w takie wystąpienie, użyj **_mbsnbcoll —** zamiast **_mbsnbcmp —**; Aby sprawdzić tylko pod względem równości ciągu, użyj **_mbsnbcmp —**.

Ponieważ **coll** funkcje sortowanie ciągów lexicographically do porównania, podczas gdy **cmp** funkcji po prostu testu równości ciąg **coll** są funkcje znacznie mniejsza niż odpowiadający mu **cmp** wersji. W związku z tym **coll** funkcje powinny być używane tylko wtedy, gdy ma różnicy między kolejność zestaw znaków i kolejność lexicographic znaków w bieżącej stronie kodowej i różnica jest przydatne do porównania.

Wartość wyjściowa jest zagrożony ustawienie **lc_ctype —** ustawienie kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez **_l** Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych Przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

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

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
