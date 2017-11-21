---
title: "Nazwy lokalne, języki i ciągi Kraj Region | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.strings
dev_langs: C++
helpviewer_keywords:
- country/region strings
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 54a309b75d5e6b1773b7dd9bb294a1538397fd05
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="locale-names-languages-and-countryregion-strings"></a>Nazwy lokalne, języki i ciągi kraj/region
*Ustawień regionalnych* argument `setlocale` i `_create_locale` funkcji można ustawić za pomocą nazwy lokalne, języki, kodów kraju/regionu i strony kodowe, które są obsługiwane przez interfejs API NLS systemu Windows. *Ustawień regionalnych* argument ma następującą postać:  
  
> *Ustawienia regionalne* :: "*nazwa_ustawienia_regionalnego*"  
&nbsp;&nbsp;&nbsp;&nbsp;| "*języka*\[\_*kraju regionu*]\[. *code_page*]] "  
&nbsp;&nbsp;&nbsp;&nbsp;| ". *code_page*"  
&nbsp;&nbsp;&nbsp;&nbsp;| "C"  
&nbsp;&nbsp;&nbsp;&nbsp;| ""  
&nbsp;&nbsp;&nbsp;&nbsp;| WARTOŚĆ NULL  
  
 Formularz Nazwa ustawień regionalnych jest preferowana; na przykład użyć `en-US` angielski (Stany Zjednoczone) lub `bs-Cyrl-BA` dla Bośniacki (cyrylica, Bośnia i Hercegowina). Zestaw nazw ustawień regionalnych jest opisany w [nazwy ustawień regionalnych](http://msdn.microsoft.com/library/windows/desktop/dd373814.aspx). Aby uzyskać listę nazw obsługiwanych ustawień regionalnych przez wersję systemu operacyjnego Windows, zobacz **nazwa kultury** kolumny [dokumentacja interfejsu API National obsługi Language (NLS)](https://www.microsoft.com/resources/msdn/goglobal/default.mspx). Ten zasób zawiera listę obsługiwanych części nazw ustawień regionalnych: języka, alfabetu i regionu. Aby uzyskać informacje na temat nazw obsługiwanych ustawień regionalnych, które mają innych niż domyślne sortowanie zleceń, zobacz **Nazwa ustawień regionalnych** kolumny w [identyfikatory kolejność sortowania](http://msdn.microsoft.com/library/windows/desktop/dd374060.aspx). Aby uzyskać dodatkowe informacje na temat obsługi language i lokalizacji w systemie operacyjnym Windows w wersji, zobacz [dodatek A: produktu zachowanie](http://msdn.microsoft.com/goglobal/bb896001.aspx) w [MS-LCID]: odwołanie do identyfikatora kodu języka systemu Windows (LCID). W systemie Windows 10 lub nowszego nazwy ustawień regionalnych, które odpowiadają prawidłowych tagów języka BCP 47 są dozwolone. Na przykład `jp-US` jest poprawny tag BCP 47, ale jest efektywne tylko `US` funkcji ustawień regionalnych.  
  
 *Języka*[*_country_region*[. *code_page*]] formularza są przechowywane w ustawień regionalnych dla kategorii, gdy ciąg języka lub ciąg języka i ciągu kraj/region, służy do tworzenia ustawień regionalnych. Zestaw ciągów obsługiwanym językiem jest opisany w [ciągi języka](../c-runtime-library/language-strings.md), a lista ciągi kraj/region obsługiwanych znajduje się w [ciągi Kraj/Region](../c-runtime-library/country-region-strings.md). Jeśli określony język nie jest skojarzony z określonym krajem/regionem, język domyślny dla określonego kraju/regionu jest przechowywany w ustawieniach regionalnych. Nie zaleca się tej formy dla ciągów ustawień regionalnych osadzonych w kodzie lub szeregowanych w pamięci, ponieważ jest bardziej prawdopodobne, że aktualizacja systemu operacyjnego je zmieni, w przeciwieństwie do formy nazwy ustawień regionalnych.  
  
 Strona kodowa to strona kodowa ANSI/OEM skojarzona z ustawieniami regionalnymi. Strona kodowa jest określana automatycznie po określeniu ustawień regionalnych za pomocą wyłącznie języka lub języka i kraju/regionu. Specjalna wartość `.ACP` Określa stronę kodową ANSI w kraju/regionie. Specjalna wartość `.OCP` Określa stronę kodową OEM w kraju/regionie. Na przykład jeśli określisz `"Greek_Greece.ACP"` jako ustawienia regionalne, ustawienia regionalne są przechowywane jako `Greek_Greece.1253` (ANSI strony kodowej grecki), i jeśli określisz `"Greek_Greece.OCP"` jako ustawień regionalnych, są przechowywane jako `Greek_Greece.737` (OEM strony kodowej grecki). Aby uzyskać więcej informacji na temat stron kodowych, zobacz [stron kodowych](../c-runtime-library/code-pages.md). Aby uzyskać listę stron kodowych obsługiwanych w systemie Windows, zobacz [kodu strony identyfikatory](http://msdn.microsoft.com/library/windows/desktop/dd317756.aspx).  
  
 Jeśli do określenia ustawień regionalnych używasz tylko strony kodowej, używany jest domyślny język i kraj/region. Na przykład jeśli określisz `".1254"` (ANSI turecki) jako lokalizacji w systemie, który skonfigurowano na język angielski (Stany Zjednoczone), ustawienia regionalne, który jest przechowywany jest `English_United States.1254`. Nie zaleca się tej formy, ponieważ może to prowadzić do niespójnego zachowania.  
  
A *ustawień regionalnych* wartość argumentu `C` określa minimalne środowisko zgodnych ANSI C tłumaczenia. `C` Ustawień regionalnych przy założeniu, że każdy `char` — typ danych jest 1 bajt i jego wartość jest zawsze mniej niż 256. Jeśli *ustawień regionalnych* punktów na pusty ciąg, ustawienia regionalne są zdefiniowane w implementacji środowiska macierzystego.  
  
Można określić wszystkie kategorie regionalne w tym samym czasie dla `setlocale` i `_wsetlocale` funkcji przy użyciu `LC_ALL` kategorii. Kategorie można ustawić na te same ustawienia regionalne lub każdą kategorię można ustawić indywidualnie przy użyciu argumentu ustawień regionalnych, który ma tę formę:  
  
> LC_ALL_specifier:: ustawień regionalnych  
&nbsp;&nbsp;&nbsp;&nbsp;| [Lc_collate — ustawienia regionalne =] [; Lc_ctype — ustawienia regionalne =] [; Lc_monetary — ustawienia regionalne =] [; Lc_numeric — ustawienia regionalne =] [; Lc_time — ustawienia regionalne =]  
  
Można określić wiele typów kategorii, oddzielając je średnikami. Typy kategorii, które nie są określone, używają bieżących ustawień regionalnych. Na przykład następujący fragment kodu ustawia bieżące ustawienia regionalne dla wszystkich kategorii do `de-DE`, a następnie ustawia kategorie `LC_MONETARY` do `en-GB` i `LC_TIME` do `es-ES`:  
  
```C  
_wsetlocale(LC_ALL, L"de-DE");  
_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki wykonawcze języka C](../c-runtime-library/c-run-time-library-reference.md)   
 [_get_current_locale —](../c-runtime-library/reference/get-current-locale.md)   
 [setLocale, _wsetlocale —](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [Ciągi języka](../c-runtime-library/language-strings.md)   
 [Ciągi Kraj/Region](../c-runtime-library/country-region-strings.md)