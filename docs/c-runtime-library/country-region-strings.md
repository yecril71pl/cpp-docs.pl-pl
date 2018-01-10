---
title: "Ciągi Kraj Region | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.strings
dev_langs: C++
helpviewer_keywords: country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94ad99ebd05fa9e37a56f2e12818f30f1f4b1212
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="countryregion-strings"></a>Ciągi kraj/region
Ciągi kraj lub region można łączyć z ciągiem języka Aby utworzyć specyfikację ustawień regionalnych dla `setlocale`, `_wsetlocale`, `_create_locale`, i `_wcreate_locale` funkcji. Dla listy nazw kraju/regionu, które są obsługiwane przez różne wersje systemu operacyjnego Windows, temacie [dokumentacja interfejsu API National obsługi Language (NLS)](https://www.microsoft.com/resources/msdn/goglobal/default.mspx). Na listach ciąg kraj/region może być dowolna z wartości kraju w **ustawień regionalnych - języka Kraj/Region** kolumny lub dowolnym skróty w **skrót nazwę kraju lub regionu** kolumny. Język dodatkowe informacje pomocy w systemach operacyjnych Windows w wersji, zobacz [dodatek A: produktu zachowanie](http://msdn.microsoft.com/goglobal/bb896001.aspx) w [MS-LCID]: odwołanie do identyfikatora kodu języka systemu Windows (LCID).  
  
 Implementacja biblioteki wykonawczej języka C obsługuje również następujące ciągi kraj/region dodatkowe i skrótów:  
  
|Ciąg kraj/region|Skrót|Nazwa ustawień regionalnych równoważne|  
|----------------------------|------------------|----------------------------|  
|Ameryka|USA|EN US|  
|Brytania|GBR|pl pl.|  
|Chin|CHN|zh-CN|  
|Czeski|CZE|cs-CZ|  
|Anglii|GBR|pl pl.|  
|Wielka Brytania|GBR|pl pl.|  
|Holandia|NLD|NL-NL|  
|Hongkong SAR|HKG|zh-HK|  
|Nowa Zelandia|NZL|EN NZ|  
|NZ|NZL|EN NZ|  
|Oczyść Chin|CHN|zh-CN|  
|Oczyść Chin|CHN|zh-CN|  
|Portoryko|PRI|Oczyść ES|  
|Słowacki|SVK|sk SK|  
|Republika Południowej Afryki|ZAF|AF ZA|  
|korea Południowa|KOR|ko-KR|  
|Republika Południowej Afryki|ZAF|AF ZA|  
|korea Południowa|KOR|ko-KR|  
|Trynidad i tobago|ABY|EN TT|  
|Wielka Brytania|GBR|pl pl.|  
|Zjednoczone Królestwo|GBR|pl pl.|  
|Stany Zjednoczone|USA|EN US|  
|US|USA|EN US|  
  
## <a name="see-also"></a>Zobacz też  
 [Nazwy lokalne, języki i ciągi Kraj/Region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Ciągi języka](../c-runtime-library/language-strings.md)   
 [setLocale, _wsetlocale —](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)