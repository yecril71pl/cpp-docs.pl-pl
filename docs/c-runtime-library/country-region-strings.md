---
title: Ciągi kraju/regionu
ms.date: 11/04/2016
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: ea0ac6ab89179683d04f6b6233c6fa1996e51a1f
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373570"
---
# <a name="countryregion-strings"></a>Ciągi kraj/region

Ciągi kraju i regionu można łączyć z ciągiem języka, aby utworzyć specyfikację ustawień regionalnych dla `setlocale` funkcji, `_wsetlocale` , `_create_locale` i `_wcreate_locale` . W przypadku list nazw krajów i regionów obsługiwanych przez różne wersje systemu operacyjnego Windows Zapoznaj się z kolumnami **Language**, **Location**i **Language tag** tabeli w [dodatku A: zachowanie produktu](https://docs.microsoft.com/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c) w \[ MS-LCID]: informacje o identyfikatorze kodu języka (LCID) systemu Windows. Przykład kodu, który wylicza dostępne nazwy ustawień regionalnych i powiązane wartości, można znaleźć w temacie [NLS: Omówienie interfejsów API opartych na nazwach](/windows/win32/intl/nls--name-based-apis-sample).

## <a name="additional-supported-country-and-region-strings"></a>Dodatkowe obsługiwane ciągi krajów i regionów

Implementacja biblioteki wykonawczej Microsoft C obsługuje również następujące dodatkowe ciągi kraju/regionu i skróty:

|Ciąg kraju/regionu|Skrót|Równoważna Nazwa ustawień regionalnych|
|----------------------------|------------------|----------------------------|
|USA|USA|pl-PL|
|Brytanii|GBR|en-GB|
|Chinach|CHN|zh-CN|
|Czeski|CZE|cs-CZ|
|Anglii|GBR|en-GB|
|Wielka Brytania|GBR|en-GB|
|Holland|NLD|nl-NL|
|Hongkong|HKG|zh-HK|
|Nowa Zelandia|NZL|EN-NZ|
|NZ|NZL|EN-NZ|
|Chiny (PR)|CHN|zh-CN|
|PR — Chiny|CHN|zh-CN|
|Portoryko — Portoryko|PRI|ES — PR|
|Słowacki|SVK|sk-SK|
|Republika Południowej Afryki|ZAF|AF — za|
|Korea Południowa|KOR|ko-KR|
|Republika Południowej Afryki|ZAF|AF — za|
|Korea Południowa|KOR|ko-KR|
|Trinidad & Tobago|Aby|pl-TT|
|Południowe Zjednoczone Królestwo|GBR|en-GB|
|Zjednoczone Królestwo|GBR|en-GB|
|Stany Zjednoczone|USA|pl-PL|
|Prześlij|USA|pl-PL|

## <a name="see-also"></a>Zobacz też

[Nazwy lokalne, Języki i ciągi kraj/region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Ciągi języka](../c-runtime-library/language-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
