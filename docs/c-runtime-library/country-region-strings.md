---
title: Ciągi Kraj / Region
ms.date: 11/04/2016
f1_keywords:
- c.strings
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: 3a3bbe9d1278cf733bafbeb23efcb0a1ad577228
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344697"
---
# <a name="countryregion-strings"></a>Ciągi kraj/region

Ciągi kraju i regionu można połączyć z ciągiem języka, aby utworzyć specyfikację ustawień regionalnych `setlocale`, `_wsetlocale`, `_create_locale`, i `_wcreate_locale` funkcji. W przypadku list nazw kraju i regionu, które są obsługiwane przez różne wersje systemu operacyjnego Windows, zobacz **języka**, **lokalizacji**, i **tagu języka** kolumn tabelę [dodatek A: Zachowanie produktu](https://msdn.microsoft.com/library/cc233982.aspx) w [MS-LCID]: Dokumentacja identyfikator (LCID) Windows języka kodu. Na przykład kod, który wylicza dostępnych nazw ustawień regionalnych i powiązane wartości zobacz [NLS: Na podstawie nazwy przykładowe interfejsów API](/windows/desktop/intl/nls--name-based-apis-sample).

## <a name="additional-supported-country-and-region-strings"></a>Dodatkowe obsługiwanych ciągów kraju i regionu

Implementacja biblioteki wykonawczej C firmy Microsoft obsługuje również następujące ciągi dodatkowe kraju/regionu i skróty:

|Ciąg kraju/regionu|Skrót|Nazwy ustawień regionalnych równoważne|
|----------------------------|------------------|----------------------------|
|Stany Zjednoczone|Stany Zjednoczone|en-US|
|Brytanii|GBR|en-GB|
|Chiny|CHN|zh-CN|
|Czeski|CZE|cs-CZ|
|w Anglii|GBR|en-GB|
|Wielka Brytania|GBR|en-GB|
|Holandia|NLD|NL-NL|
|SRA Hongkong|HKG|zh-HK|
|new-zealand|NZL|EN NZ|
|nz|NZL|EN NZ|
|Chiny (pr)|CHN|zh-CN|
|Chiny (pr)|CHN|zh-CN|
|Portoryko|PRI|es-PR|
|Słowacki|SVK|sk-SK|
|Republika Południowej Afryki|ZAF|af-ZA|
|korea Południowa|KOR|ko-KR|
|Republika Południowej Afryki|ZAF|af-ZA|
|korea Południowa|KOR|ko-KR|
|Trynidad i tobago|TTO|en-TT|
|Zjednoczone Królestwo|GBR|en-GB|
|Zjednoczone Królestwo|GBR|en-GB|
|Stany Zjednoczone|Stany Zjednoczone|en-US|
|us|Stany Zjednoczone|en-US|

## <a name="see-also"></a>Zobacz także

[Nazwy lokalne, języki i ciągi Kraj/Region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Ciągi języka](../c-runtime-library/language-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
