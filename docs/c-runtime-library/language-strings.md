---
title: Ciągi języka
ms.date: 11/04/2016
f1_keywords:
- c.strings
helpviewer_keywords:
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
ms.openlocfilehash: 143f06a0cf22265734d6d77f8fca4efd5ac3031b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62343163"
---
# <a name="language-strings"></a>Ciągi języka

[Setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) i [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) funkcji można użyć języków Windows API NLS obsługiwanych systemach operacyjnych, które nie korzystają z strony kodowej Unicode. Aby uzyskać listę obsługiwanych języków przez wersję systemu operacyjnego, zobacz [dodatek A: Zachowanie produktu](https://msdn.microsoft.com/library/cc233982.aspx) w [MS-LCID]: Dokumentacja identyfikator (LCID) Windows języka kodu. Ciąg języka może być dowolną z wartości w **języka** i **tagu języka** kolumn listę obsługiwanych języków. Na przykład kod, który wylicza dostępnych nazw ustawień regionalnych i powiązane wartości zobacz [NLS: Na podstawie nazwy przykładowe interfejsów API](/windows/desktop/intl/nls--name-based-apis-sample).

## <a name="additional-supported-language-strings"></a>Dodatkowe obsługiwanych ciągów języka

Implementacja biblioteki wykonawczej C firmy Microsoft obsługuje również następujące ciągi języka:

|Ciąg języka|Nazwy ustawień regionalnych równoważne|
|---------------------|----------------------------|
|American|en-US|
|angielski|en-US|
|— angielski|en-US|
|australijskie|EN-AU|
|Belgii|nl-BE|
|kanadyjski|EN-CA|
|CHH|zh-HK|
|chi|zh-SG|
|Chiński|nazwy zh|
|chiński — hongkong|zh-HK|
|chiński uproszczony|zh-CN|
|chiński — Singapur|zh-SG|
|chiński tradycyjny|zh-TW|
|Holenderski — Belgia|nl-BE|
|angielskiego amerykańskiego|en-US|
|jednostki alokacji na angielski|EN-AU|
|angielski — belize|en-BZ|
|angielski — może|EN-CA|
|Angielski — Karaiby|en-029|
|angielski — wygasnąć|EN-IE|
|Angielski — Jamajka|en-JM|
|angielski — nz|EN NZ|
|angielski — Republika Południowej Afryki|en-ZA|
|Angielski — Trynidad y tobago|en-TT|
|angielski — Zjednoczone Królestwo|en-GB|
|angielski — us|en-US|
|Angielski — Stany Zjednoczone|en-US|
|Francuski — Belgia|fr-BE|
|French-Canadian|fr-CA|
|Francuski (Luksemburg)|fr-LU|
|Francuski swiss|FR-CH|
|german-austrian|de-AT|
|german-lichtenstein|de-LI|
|Niemiecki — Luksemburg|de-LU|
|Niemiecki — Szwajcaria|de-CH|
|irlandzki — angielski|EN-IE|
|Włoski — Szwajcaria|it-CH|
|Norweski|Brak|
|Norweski bokmal|nb-NO|
|norwegian-nynorsk|nn-NO|
|Portugalski — Brazylia|pt-BR|
|Argentyna hiszpański|ES AR|
|Boliwia hiszpański|es-BO|
|Hiszpański — chile|ES-CL|
|Hiszpański — Kolumbia|ES CO|
|Hiszpański — Kostaryka|ES CR|
|Republika Dominikańska hiszpański|es-DO|
|Ekwador hiszpański|es-EC|
|Hiszpański Salwador|es-SV|
|Hiszpański — Gwatemala|es-GT|
|Hiszpański honduras|ES HN|
|Hiszpański Meksykańskich|es-MX|
|Nowoczesny hiszpański|es-ES|
|Hiszpański — Nikaragua|es-NI|
|Hiszpański panama|es-PA|
|Paragwaj hiszpański|es-PY|
|Hiszpański — peru|es-PE|
|Hiszpański Portoryko|es-PR|
|Urugwaj hiszpański|ES UY|
|Wenezuela hiszpański|es-VE|
|szwedzki — Finlandia|sv-FI|
|Szwajcaria|de-CH|
|Zjednoczone Królestwo|en-GB|
|us|en-US|
|usa|en-US|

## <a name="see-also"></a>Zobacz także

[Nazwy lokalne, języki i ciągi Kraj/Region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Ciągi Kraj/Region](../c-runtime-library/country-region-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
