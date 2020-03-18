---
title: Ciągi kraju/regionu
ms.date: 11/04/2016
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: 8556e005618a1b69c47498a07e218284dcb1164f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443431"
---
# <a name="countryregion-strings"></a>Ciągi kraj/region

Ciągi kraju i regionu można łączyć z ciągiem języka, aby utworzyć specyfikację ustawień regionalnych dla funkcji `setlocale`, `_wsetlocale`, `_create_locale`i `_wcreate_locale`. W przypadku list nazw krajów i regionów obsługiwanych przez różne wersje systemu operacyjnego Windows Zapoznaj się z kolumnami **Language**, **Location**i **Language tag** tabeli w [dodatku A: zachowanie produktu](https://msdn.microsoft.com/library/cc233982.aspx) w [MS-LCID]: informacje o identyfikatorze kodu języka (LCID) systemu Windows. Przykład kodu, który wylicza dostępne nazwy ustawień regionalnych i powiązane wartości, można znaleźć w temacie [NLS: Omówienie interfejsów API opartych na nazwach](/windows/win32/intl/nls--name-based-apis-sample).

## <a name="additional-supported-country-and-region-strings"></a>Dodatkowe obsługiwane ciągi krajów i regionów

Implementacja biblioteki wykonawczej Microsoft C obsługuje również następujące dodatkowe ciągi kraju/regionu i skróty:

|Ciąg kraju/regionu|Skrót|Równoważna Nazwa ustawień regionalnych|
|----------------------------|------------------|----------------------------|
|Stany Zjednoczone|Stany Zjednoczone|pl-PL|
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
|Trinidad & Tobago|Aby|pl-TT|
|Zjednoczone Królestwo|GBR|en-GB|
|Zjednoczone Królestwo|GBR|en-GB|
|Stany Zjednoczone|Stany Zjednoczone|pl-PL|
|Prześlij|Stany Zjednoczone|pl-PL|

## <a name="see-also"></a>Zobacz też

[Nazwy lokalne, Języki i ciągi kraj/region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Ciągi języka](../c-runtime-library/language-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
