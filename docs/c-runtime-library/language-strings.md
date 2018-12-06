---
title: Ciągi języka
ms.date: 11/04/2016
f1_keywords:
- c.strings
helpviewer_keywords:
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
ms.openlocfilehash: 143f06a0cf22265734d6d77f8fca4efd5ac3031b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620288"
---
# <a name="language-strings"></a>Ciągi języka

[Setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) i [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) funkcji można użyć języków Windows API NLS obsługiwanych systemach operacyjnych, które nie korzystają z strony kodowej Unicode. Aby uzyskać listę obsługiwanych języków przez wersję systemu operacyjnego, zobacz [dodatek A: produktu zachowanie](https://msdn.microsoft.com/library/cc233982.aspx) w [MS-LCID]: odwołanie do Windows języka kodu identyfikator (LCID). Ciąg języka może być dowolną z wartości w **języka** i **tagu języka** kolumn listę obsługiwanych języków. Na przykład kod, który wylicza dostępnych nazw ustawień regionalnych i powiązane wartości zobacz [NLS: Przykładowe interfejsów API na podstawie nazwy](/windows/desktop/intl/nls--name-based-apis-sample).

## <a name="additional-supported-language-strings"></a>Dodatkowe obsługiwanych ciągów języka

Implementacja biblioteki wykonawczej C firmy Microsoft obsługuje również następujące ciągi języka:

|Ciąg języka|Nazwy ustawień regionalnych równoważne|
|---------------------|----------------------------|
|American|pl pl|
|angielski|pl pl|
|— angielski|pl pl|
|australijskie|EN-AU|
|Belgii|Holandia — być|
|kanadyjski|EN-CA|
|CHH|zh-HK|
|CHI|zh-SG|
|Chiński|nazwy zh|
|chiński — SRA Hongkong|zh-HK|
|chiński uproszczony|zh-CN|
|chiński — Singapur|zh-SG|
|chiński tradycyjny|zh-TW|
|Holenderski — Belgia|Holandia — być|
|angielskiego amerykańskiego|pl pl|
|jednostki alokacji na angielski|EN-AU|
|angielski — belize|EN BZ|
|angielski — może|EN-CA|
|Angielski — Karaiby|EN-029|
|angielski — wygasnąć|EN-IE|
|Angielski — Jamajka|EN JM|
|angielski — nz|EN NZ|
|angielski — Republika Południowej Afryki|EN ZA|
|Angielski — Trynidad y tobago|EN TT|
|angielski — Zjednoczone Królestwo|en-GB|
|angielski — us|pl pl|
|Angielski — Stany Zjednoczone|pl pl|
|Francuski — Belgia|FR — być|
|French-Canadian|fr-CA|
|Francuski (Luksemburg)|FR LU|
|Francuski swiss|FR-CH|
|Niemiecki — Austria|de-AT|
|niemiecki Liechtensteinu|de-LI|
|Niemiecki — Luksemburg|de LU|
|Niemiecki — Szwajcaria|de-CH|
|irlandzki — angielski|EN-IE|
|Włoski — Szwajcaria|IT CH|
|Norweski|Brak|
|Norweski bokmal|nb-NO|
|Norweski nynorsk|Brak nn|
|Portugalski — Brazylia|pt-BR|
|Argentyna hiszpański|ES AR|
|Boliwia hiszpański|ES BO|
|Hiszpański — chile|ES-CL|
|Hiszpański — Kolumbia|ES CO|
|Hiszpański — Kostaryka|ES CR|
|Republika Dominikańska hiszpański|CZY ES|
|Ekwador hiszpański|ES WE.|
|Hiszpański Salwador|ES SV|
|Hiszpański — Gwatemala|ES >|
|Hiszpański honduras|ES HN|
|Hiszpański Meksykańskich|es-MX|
|Nowoczesny hiszpański|es-ES|
|Hiszpański — Nikaragua|ES-NI|
|Hiszpański panama|ES PA|
|Paragwaj hiszpański|ES-PY|
|Hiszpański — peru|ES PE|
|Hiszpański Portoryko|ES (PR)|
|Urugwaj hiszpański|ES UY|
|Wenezuela hiszpański|ES VE|
|szwedzki — Finlandia|SV-FI|
|Szwajcaria|de-CH|
|Zjednoczone Królestwo|en-GB|
|USA|pl pl|
|Stany Zjednoczone|pl pl|

## <a name="see-also"></a>Zobacz także

[Nazwy lokalne, języki i ciągi Kraj/Region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Ciągi Kraj/Region](../c-runtime-library/country-region-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
