---
title: Ciągi języka | Dokumentacja firmy Microsoft
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
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92ad129a5703f509cfd9543497cceffae3a6e7b3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="language-strings"></a>Ciągi języka
`setlocale` i `_create_locale` funkcji można użyć interfejsu API NLS systemu Windows obsługiwane języki w systemach operacyjnych, które nie korzystają z strony kodowej Unicode. Aby uzyskać listę języków obsługiwanych przez wersję systemu operacyjnego, zobacz [dokumentacja interfejsu API National obsługi Language (NLS)](https://www.microsoft.com/resources/msdn/goglobal/default.mspx). Ciąg języka może być dowolna z wartości w **języka** i **skrót nazwy języka** kolumn listę obsługiwanych języków. Aby uzyskać dodatkowe informacje na temat obsługi języków przez wersję systemu operacyjnego, zobacz [dodatek A: produktu zachowanie](http://msdn.microsoft.com/goglobal/bb896001.aspx) w [MS-LCID]: odwołanie do identyfikatora kodu języka systemu Windows (LCID).   
  
Implementacja biblioteki wykonawczej języka C obsługuje także te ciągi języka:  
  
|Ciąg języka|Nazwa ustawień regionalnych równoważne|  
|---------------------|----------------------------|  
|American|EN US|  
|angielski|EN US|  
|alfabecie angielskim|EN US|  
|Australian|EN-AU|  
|Belgijski|NL-być|  
|kanadyjscy|EN-CA|  
|CHH|zh-HK|  
|CHI|zh-SG|  
|Chiński|zh|  
|chiński Hongkongu|zh-HK|  
|chiński uproszczony|zh-CN|  
|chiński Singapuru|zh-SG|  
|chiński tradycyjny|zh-TW|  
|holenderski Belgijskie|NL-być|  
|amerykański angielski|EN US|  
|aus angielski|EN-AU|  
|belize angielski|EN BZ|  
|może angielski|EN-CA|  
|Karaibów angielski|EN-029|  
|ire angielski|EN-IE|  
|Jamajka angielski|EN JM|  
|nz angielski|EN NZ|  
|angielski Południowej Afryki|EN-ZA-|  
|Trynidad angielski y tobago|EN TT|  
|Wielka Brytania angielski|pl pl.|  
|angielski-us|EN US|  
|angielski usa|EN US|  
|Francuski Belgijskie|FR — można|  
|French-Canadian|fr-CA|  
|Francuski Luksemburgu|FR LU|  
|Francuski Szwajcaria|FR CH|  
|niemiecki austriackiej|Niemcy AT|  
|niemiecki Liechtensteinu|Niemcy LI|  
|niemiecki Luksemburgu|Niemcy LU|  
|Niemiecki Szwajcaria|Niemcy CH|  
|angielski Irlandii|EN-IE|  
|Włoski Szwajcaria|IT CH|  
|Norweski|Brak|  
|Norweski bokmal|nb-NO|  
|Norweski nynorsk|NR nn|  
|Portugalski — Brazylia|pt-BR|  
|Hiszpański Argentyny|ES AR|  
|Hiszpański Boliwii|ES BO|  
|podrzędnej lokacji hiszpański|ES-CL|  
|Hiszpański Kolumbii|ES CO|  
|Hiszpański Kostaryka|ES CR|  
|Hiszpański Dominikana|CZY ES|  
|Hiszpański Ekwador|WE ES|  
|Hiszpański Salwador|ES SV|  
|Hiszpański Gwatemali|ES >|  
|Hiszpański Hondurasu|ES HN|  
|Hiszpański Meksykańskimi|es-MX|  
|Hiszpański modern|es-ES|  
|Hiszpański Nikaragua|ES NI|  
|Hiszpański Panamy|ES PA|  
|Hiszpański Paragwaju|Kopiuj ES|  
|Hiszpański peru|ES PE|  
|Hiszpański Portoryko|Oczyść ES|  
|Hiszpański Urugwajskiej|ES UY|  
|Hiszpański Wenezueli|PISZ ES|  
|szwedzki Finlandia|SV-FI|  
|Szwajcaria|Niemcy CH|  
|Wielka Brytania|pl pl.|  
|US|EN US|  
|USA|EN US|  
  
## <a name="see-also"></a>Zobacz też  
 [Nazwy lokalne, języki i ciągi Kraj/Region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Ciągi Kraj/Region](../c-runtime-library/country-region-strings.md)   
 [setLocale, _wsetlocale —](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)