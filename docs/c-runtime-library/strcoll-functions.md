---
title: strcoll — Funkcje
ms.date: 11/04/2016
apilocation:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- strcoll
helpviewer_keywords:
- code pages, using for string comparisons
- string comparison [C++], culture-specific
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: c09eeff3-8aba-4cfb-a524-752436d85573
ms.openlocfilehash: c6b4b45184ea4cc3320f3de069884ac084c7cfcd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450235"
---
# <a name="strcoll-functions"></a>strcoll — Funkcje

Każdy z `strcoll` i `wcscoll` funkcji porównuje dwa ciągi zgodnie z opisem w `LC_COLLATE` strona kodowa ustawień lokalnych, obecnie w użyciu ustawienia kategorii. Każdy z `_mbscoll` funkcji porównuje dwa ciągi zgodnie z aktualnie używaną stroną kodową wielobajtowe. Użyj `coll` funkcji w celu porównania ciągów, gdy istnieje różnica pomiędzy kolejnością zestawu znaków i kolejnością znaków leksykograficznych w bieżącej stronie kodowej, a różnica ta ma znaczenie dla porównania. Użyć odpowiedniego `cmp` funkcji do testowania tylko ciąg znaków równości.

### <a name="strcoll-functions"></a>strcoll — Funkcje

|SBCS|Unicode|MBCS|Opis|
|----------|-------------|----------|-----------------|
|[strcoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[wcscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[_mbscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|Porównuje dwa ciągi|
|[_stricoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_wcsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_mbsicoll —](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|Porównuje dwa ciągi (wielkich liter)|
|[_strncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_wcsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_mbsncoll —](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|COLLATE — najpierw `count` z dwóch ciągów znaków|
|[_strnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_wcsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_mbsnicoll —](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|COLLATE — najpierw `count` znaki z dwóch ciągów (bez uwzględniania wielkości liter)|

## <a name="remarks"></a>Uwagi

Znaków jednobajtowych (SBCS) wersje tych funkcji (`strcoll`, `stricoll`, `_strncoll`, i `_strnicoll`) porównać `string1` i `string2` zgodnie z opisem w `LC_COLLATE` kategorii ustawienia bieżącego ustawienia regionalnego. Funkcje te różnią się od odpowiadających im `strcmp` funkcje, w tym `strcoll` funkcje używają kodu strony informacji o ustawieniach regionalnych zapewniająca sekwencji sortowania. Dla porównania ciągów ustawień regionalnych, w których kolejność zestawu znaków i kolejnością znaków leksykograficznych różnią się `strcoll` funkcje powinny być używane zamiast odpowiednich `strcmp` funkcji. Aby uzyskać więcej informacji na temat `LC_COLLATE`, zobacz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

Dla niektórych stron kodowych i odpowiednich zestawów znaków kolejności znaków w zestawie znaków mogą się różnić z kolejnością znaków leksykograficznych. W ustawieniach regionalnych "języka C", nie jest przypadek: kolejność znaków w zestawie znaków ASCII jest taka sama, jak w porządku leksykograficznym znaków. Jednak w niektórych stron kodowych Europejskich, na przykład znak "" (wartość 0x61) poprzedza znak "ź" (wartość 0xE4) znak ustawiane, ale znak "ź" poprzedza znak "" leksykograficznie. Aby przeprowadzić porównanie leksykograficznych w takiej sytuacji, należy użyć `strcoll` zamiast `strcmp`. Alternatywnie, można użyć `strxfrm` oryginalnego ciągów i następnie używać `strcmp` na ciągi wynikowe.

`strcoll`, `stricoll`, `_strncoll`, i `_strnicoll` automatycznie obsługiwać ciągi znaków wielobajtowych według strona kodowa ustawień lokalnych, obecnie w użyciu, jak ich odpowiedniki znaków dwubajtowych (Unicode). Znaków wielobajtowych (MBCS) wersje tych funkcji, jednak zestawiają ciągi, na podstawie znaków zgodnie z aktualnie używaną stroną kodową wielobajtowe.

Ponieważ `coll` funkcje zestawiają ciągi leksykograficznie dla celów porównawczych, natomiast `cmp` funkcje po prostu testują dla równości ciągu, `coll` funkcje są znacznie wolniejsze niż odpowiadające `cmp` wersji. W związku z tym `coll` funkcje powinny być używane tylko wtedy, gdy istnieje różnica pomiędzy kolejnością zestawu znaków i kolejnością znaków leksykograficznych w bieżącej stronie kodowej, a różnica ta ma znaczenie dla porównania ciągu.

## <a name="see-also"></a>Zobacz też

[Wersja regionalna](../c-runtime-library/locale.md)<br/>
[Manipulowanie ciągami](../c-runtime-library/string-manipulation-crt.md)<br/>
[localeconv](../c-runtime-library/reference/localeconv.md)<br/>
[_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l](../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[strcmp, wcscmp, _mbscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)