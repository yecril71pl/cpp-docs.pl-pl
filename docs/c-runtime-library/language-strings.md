---
title: Ciągi języka
ms.date: 11/04/2016
f1_keywords:
- c.strings
helpviewer_keywords:
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
ms.openlocfilehash: a9e6eaa65516b5b49022526f24e220dec83b2c26
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500073"
---
# <a name="language-strings"></a>Ciągi języka

Funkcje [](../c-runtime-library/reference/setlocale-wsetlocale.md) setlocale i [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) mogą używać obsługiwanych języków NLS API systemu Windows w systemach operacyjnych, które nie korzystają ze strony kodowej Unicode. Aby uzyskać listę obsługiwanych języków według wersji systemu operacyjnego, zobacz [dodatek a: Zachowanie](https://msdn.microsoft.com/library/cc233982.aspx) produktu w [MS-LCID]: Dokumentacja identyfikatora kodu języka (LCID) systemu Windows. Ciąg języka może być dowolną wartością w kolumnach **Język** i **Język** listy obsługiwanych języków. Przykład kodu, który wylicza dostępne nazwy ustawień regionalnych i powiązane wartości, można znaleźć w [temacie NLS: Przykład](/windows/win32/intl/nls--name-based-apis-sample)interfejsów API opartych na nazwach.

## <a name="additional-supported-language-strings"></a>Dodatkowe obsługiwane ciągi języka

Implementacja biblioteki wykonawczej Microsoft C obsługuje również następujące ciągi języka:

|Ciąg języka|Równoważna Nazwa ustawień regionalnych|
|---------------------|----------------------------|
|Samoa|en-US|
|angielski (amerykański)|en-US|
|amerykański (angielski)|en-US|
|służb|EN-AU|
|Belgii|nl-BE|
|Ustawa|EN-CA|
|chh|zh-HK|
|rozkład Chi|zh-SG|
|Chiński|zh|
|Chiński — SRA Hongkong|zh-HK|
|Chiński (uproszczony)|zh-CN|
|Chiński (Singapur)|zh-SG|
|Chiński (tradycyjny)|zh-TW|
|holenderski — belgijski|nl-BE|
|angielski (amerykański)|en-US|
|angielski (Australia)|EN-AU|
|angielski — Belize|en-BZ|
|angielski — może|EN-CA|
|angielski — Karaiby|en-029|
|angielski — wygasnąć|EN-IE|
|Angielski — Jamajka|pl-JM|
|angielski — NZ|EN NZ|
|angielski (Republika Południowej Afryki)|pl-za|
|angielski — Trynidad y Tobago|pl-TT|
|angielski — Zjednoczone Królestwo|en-GB|
|angielski — Stany Zjednoczone|en-US|
|angielski (USA)|en-US|
|francuski — belgijski|fr-BE|
|francuski — Kanada|fr-CA|
|Francuski — Luksemburg|fr — LU|
|francuski — szwajcarski|FR-CH|
|niemiecki — austriacki|de-AT|
|niemiecki — Lichtenstein|de-LI|
|niemiecki — Luksemburg|de-LU|
|niemiecki (Szwajcaria)|de-CH|
|Irlandzki — angielski|EN-IE|
|włoski (szwajcarski)|IT-CH|
|Norweski|znaleziono|
|norweski (Bokmal)|nb-NO|
|norweski — nynorsk|NN-NO|
|portugalski (Brazylia)|pt-BR|
|hiszpański (Argentyna)|ES-AR|
|Hiszpański — Boliwia|ES — BO|
|hiszpański — Chile|ES — CL|
|hiszpański — Kolumbia|ES — CO|
|hiszpański — Kostaryka|ES — CR|
|hiszpański — Dominikana|ES-DO|
|hiszpański (Ekwador)|ES — we|
|hiszpański — Salwador|ES — SV|
|Hiszpański — Gwatemala|es-GT|
|hiszpański — Honduras|ES — HN|
|hiszpański (Meksyk)|es-MX|
|hiszpański — nowoczesny|es-ES|
|hiszpański — Nikaragua|ES — NI|
|hiszpański — Panama|ES — PA|
|Hiszpański — Paragwaj|ES — PR|
|Hiszpański — Peru|es-PE|
|hiszpański — Portoryko|ES — PR|
|hiszpański — Urugwaj|ES — UY|
|hiszpański — Wenezuela|ES — VE|
|szwedzki — Finlandia|OHR-FI|
|przewoźnik|de-CH|
|Zjednoczone Królestwo|en-GB|
|Prześlij|en-US|
|poniżej|en-US|

## <a name="see-also"></a>Zobacz także

[Nazwy lokalne, Języki i ciągi kraj/region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Ciągi kraju/regionu](../c-runtime-library/country-region-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
