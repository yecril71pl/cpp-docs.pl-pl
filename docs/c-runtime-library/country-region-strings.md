---
title: Ciągi kraju/regionu
ms.date: 11/04/2016
f1_keywords:
- c.strings
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: 49eb6bc4473d9e54c06c3bf9290f8c3c96640415
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500246"
---
# <a name="countryregion-strings"></a>Ciągi kraj/region

Ciągi kraju i regionu można `setlocale`łączyć z ciągiem języka, aby utworzyć specyfikację ustawień regionalnych dla funkcji, `_wsetlocale`, `_create_locale`i. `_wcreate_locale` Aby uzyskać listę nazw krajów i regionów obsługiwanych przez różne wersje systemu operacyjnego Windows, zapoznaj się z kolumnami **Language**, **Location**i **Language tag** tabeli w [dodatku A. Zachowanie](https://msdn.microsoft.com/library/cc233982.aspx) produktu w [MS-LCID]: Dokumentacja identyfikatora kodu języka (LCID) systemu Windows. Przykład kodu, który wylicza dostępne nazwy ustawień regionalnych i powiązane wartości, można znaleźć w [temacie NLS: Przykład](/windows/win32/intl/nls--name-based-apis-sample)interfejsów API opartych na nazwach.

## <a name="additional-supported-country-and-region-strings"></a>Dodatkowe obsługiwane ciągi krajów i regionów

Implementacja biblioteki wykonawczej Microsoft C obsługuje również następujące dodatkowe ciągi kraju/regionu i skróty:

|Ciąg kraju/regionu|Jednostek|Równoważna Nazwa ustawień regionalnych|
|----------------------------|------------------|----------------------------|
|Stany Zjednoczone|Stany Zjednoczone|en-US|
|Brytanii|GBR|en-GB|
|Chinach|CHN|zh-CN|
|Czeski|CZE|cs-CZ|
|Anglii|GBR|en-GB|
|Wielka Brytania|GBR|en-GB|
|Holland|NLD|NL-NL|
|SRA Hongkong|HKG|zh-HK|
|Nowa Zelandia|NZL|EN NZ|
|nz|NZL|EN NZ|
|Chiny (PR)|CHN|zh-CN|
|PR — Chiny|CHN|zh-CN|
|Portoryko — Portoryko|PRI|ES — PR|
|Słowacki|SVK|sk-SK|
|Republika Południowej Afryki|ZAF|af-ZA|
|Korea Południowa|KOR|ko-KR|
|Republika Południowej Afryki|ZAF|af-ZA|
|Korea Południowa|KOR|ko-KR|
|Trinidad & Tobago|ABY|pl-TT|
|Zjednoczone Królestwo|GBR|en-GB|
|Zjednoczone Królestwo|GBR|en-GB|
|Stany Zjednoczone|Stany Zjednoczone|en-US|
|Prześlij|Stany Zjednoczone|en-US|

## <a name="see-also"></a>Zobacz także

[Nazwy lokalne, Języki i ciągi kraj/region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Ciągi języka](../c-runtime-library/language-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
