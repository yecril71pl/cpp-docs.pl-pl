---
title: Ciągi Kraj / Region | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.strings
dev_langs:
- C++
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f227feec25e3b487772f8e469651f08be825419f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605633"
---
# <a name="countryregion-strings"></a>Ciągi kraj/region

Ciągi kraju i regionu można połączyć z ciągiem języka, aby utworzyć specyfikację ustawień regionalnych `setlocale`, `_wsetlocale`, `_create_locale`, i `_wcreate_locale` funkcji. W przypadku list nazw kraju i regionu, które są obsługiwane przez różne wersje systemu operacyjnego Windows, zobacz **języka**, **lokalizacji**, i **tagu języka** kolumn tabelę [dodatek A: produktu zachowanie](https://msdn.microsoft.com/library/cc233982.aspx) w [MS-LCID]: odwołanie do Windows języka kodu identyfikator (LCID). Na przykład kod, który wylicza dostępnych nazw ustawień regionalnych i powiązane wartości zobacz [NLS: Przykładowe interfejsów API na podstawie nazwy](/windows/desktop/intl/nls--name-based-apis-sample).

## <a name="additional-supported-country-and-region-strings"></a>Dodatkowe obsługiwanych ciągów kraju i regionu

Implementacja biblioteki wykonawczej C firmy Microsoft obsługuje również następujące ciągi dodatkowe kraju/regionu i skróty:

|Ciąg kraju/regionu|Skrót|Nazwy ustawień regionalnych równoważne|
|----------------------------|------------------|----------------------------|
|Stany Zjednoczone|STANY ZJEDNOCZONE|pl pl|
|Brytanii|GBR|en-GB|
|Chiny|CHN|zh-CN|
|Czeski|CZE|cs-CZ|
|w Anglii|GBR|en-GB|
|Wielka Brytania|GBR|en-GB|
|Holandia|NLD|NL-NL|
|SRA Hongkong|HKG|zh-HK|
|Nowa Zelandia|NZL|EN NZ|
|NZ|NZL|EN NZ|
|Chiny (pr)|CHN|zh-CN|
|Chiny (pr)|CHN|zh-CN|
|Portoryko|PRI|ES (PR)|
|Słowacki|SVK|sk-SK|
|Republika Południowej Afryki|ZAF|af-ZA|
|korea Południowa|KOR|ko-KR|
|Republika Południowej Afryki|ZAF|af-ZA|
|korea Południowa|KOR|ko-KR|
|Trynidad i tobago|ABY|EN TT|
|Zjednoczone Królestwo|GBR|en-GB|
|Zjednoczone Królestwo|GBR|en-GB|
|Stany Zjednoczone|STANY ZJEDNOCZONE|pl pl|
|USA|STANY ZJEDNOCZONE|pl pl|

## <a name="see-also"></a>Zobacz także

[Nazwy lokalne, języki i ciągi Kraj/Region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)  
[Ciągi języka](../c-runtime-library/language-strings.md)  
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)  
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)  
