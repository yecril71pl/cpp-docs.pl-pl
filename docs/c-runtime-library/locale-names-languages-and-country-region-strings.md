---
title: Nazwy lokalne, języki i ciągi Kraj / Region | Dokumentacja firmy Microsoft
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
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f28262a1402d81bd5dcd0933f943b420a37f044
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606738"
---
# <a name="locale-names-languages-and-countryregion-strings"></a>Nazwy lokalne, języki i ciągi kraj/region

*Ustawień regionalnych* argument `setlocale` i `_create_locale` funkcje można ustawić za pomocą nazw ustawień regionalnych, języków, kodów krajów/regionów i stron kodowych, które są obsługiwane przez Windows NLS API. *Ustawień regionalnych* argument ma następującą postać:

> *Ustawienia regionalne* :: "*nazwa_ustawienia_regionalnego*"  
&nbsp;&nbsp;&nbsp;&nbsp;| "*języka*\[\_*kraj / region*]\[. *code_page*]] "  
&nbsp;&nbsp;&nbsp;&nbsp;| ". *code_page*"  
&nbsp;&nbsp;&nbsp;&nbsp;| "C"  
&nbsp;&nbsp;&nbsp;&nbsp;| ""  
&nbsp;&nbsp;&nbsp;&nbsp;| WARTOŚĆ NULL  

Forma nazwy ustawień regionalnych jest preferowana; na przykład użyć `en-US` dla języka angielskiego (Stany Zjednoczone) lub `bs-Cyrl-BA` dla bośniackiego (cyrylica, Bośnia i Hercegowina). Zestaw nazw ustawień regionalnych jest opisany w [nazw ustawień regionalnych](/windows/desktop/Intl/locale-names). Aby uzyskać listę nazw ustawień regionalnych obsługiwanych przez wersję systemu operacyjnego Windows, zobacz **tagu języka** kolumny tabeli w [dodatek A: produktu zachowanie](https://msdn.microsoft.com/library/cc233982.aspx) w [MS-LCID]: Windows języka kodu identyfikator (LCID) Odwołanie. Ten zasób zawiera listę obsługiwanych części nazw ustawień regionalnych: języka, alfabetu i regionu. Aby uzyskać informacje o obsługiwanych nazw ustawień regionalnych, które mają inne niż domyślne, zobacz **nazwy ustawień regionalnych** kolumny w [identyfikatory kolejności sortowania](/windows/desktop/Intl/sort-order-identifiers). W obszarze Windows 10 lub nowszym nazwy ustawień regionalnych, które odpowiadają prawidłowych tagów języka BCP 47 są dozwolone. Na przykład `jp-US` jest poprawny tag BCP 47, ale jest efektywne tylko `US` dla funkcji ustawień regionalnych.

*Języka*[*_country_region*[. *code_page*]] formularza są przechowywane w ustawieniach regionalnych dla kategorii, gdy ciąg języka lub ciąg języka i ciąg kraju/regionu jest używany do tworzenia ustawień regionalnych. Zestaw obsługiwanych ciągów języka jest opisany w [Language Strings](../c-runtime-library/language-strings.md), i listę ciągów obsługiwanych kraju/regionu znajduje się w [ciągi Kraj/Region](../c-runtime-library/country-region-strings.md). Jeśli określony język nie jest skojarzony z określonym krajem/regionem, język domyślny dla określonego kraju/regionu jest przechowywany w ustawieniach regionalnych. Nie zaleca się tej formy dla ciągów ustawień regionalnych osadzonych w kodzie lub szeregowanych w pamięci, ponieważ jest bardziej prawdopodobne, że aktualizacja systemu operacyjnego je zmieni, w przeciwieństwie do formy nazwy ustawień regionalnych.

Strona kodowa to strona kodowa ANSI/OEM skojarzona z ustawieniami regionalnymi. Strona kodowa jest określana automatycznie po określeniu ustawień regionalnych za pomocą wyłącznie języka lub języka i kraju/regionu. Specjalna wartość `.ACP` Określa stronę kodową ANSI dla kraju/regionu. Specjalna wartość `.OCP` Określa stronę kodową OEM dla kraju/regionu. Na przykład, jeśli określisz `"Greek_Greece.ACP"` jako ustawienie regionalne, ustawienie regionalne jest przechowywane jako `Greek_Greece.1253` (na stronę kodową ANSI dla języka greckiego), a jeśli określisz `"Greek_Greece.OCP"` jako ustawienie regionalne, jest przechowywany jako `Greek_Greece.737` (stronę kodową OEM dla języka greckiego). Aby uzyskać więcej informacji dotyczących stron kodowych, zobacz [stron kodowych](../c-runtime-library/code-pages.md). Aby uzyskać listę stron kodowych obsługiwanych w Windows, zobacz [kodu strony identyfikatory](/windows/desktop/Intl/code-page-identifiers).

Jeśli do określenia ustawień regionalnych używasz tylko strony kodowej, używany jest domyślny język i kraj/region. Na przykład, jeśli określisz `".1254"` (turecki ANSI) jako ustawienie regionalne w systemie, który jest skonfigurowany dla języka angielskiego (Stany Zjednoczone), ustawienia regionalne, który jest przechowywany jest `English_United States.1254`. Nie zaleca się tej formy, ponieważ może to prowadzić do niespójnego zachowania.

A *ustawień regionalnych* wartość argumentu `C` określa minimalne środowisko odpowiadające ANSI dla translacji C. `C` Ustawień regionalnych zakłada, że każdy `char` — typ danych jest 1 bajt i jego wartość jest zawsze mniejsza niż 256. Jeśli *ustawień regionalnych* wskazuje na pusty ciąg, ustawienia regionalne są natywnym środowiskiem zdefiniowanych w implementacji.

Można określić wszystkie kategorie ustawień regionalnych, w tym samym czasie dla `setlocale` i `_wsetlocale` funkcji przy użyciu `LC_ALL` kategorii. Kategorie można ustawić na te same ustawienia regionalne lub każdą kategorię można ustawić indywidualnie przy użyciu argumentu ustawień regionalnych, który ma tę formę:

> LC_ALL_specifier:: ustawień regionalnych  
&nbsp;&nbsp;&nbsp;&nbsp;| [LC_COLLATE ustawienia regionalne =] [; LC_CTYPE ustawienia regionalne =] [; LC_MONETARY ustawienia regionalne =] [; LC_NUMERIC ustawienia regionalne =] [; LC_TIME ustawienia regionalne =]

Można określić wiele typów kategorii, oddzielając je średnikami. Typy kategorii, które nie są określone, używają bieżących ustawień regionalnych. Na przykład, następujący fragment kodu ustawia bieżące ustawienia regionalne dla wszystkich kategorii na `de-DE`, a następnie ustawia kategorie `LC_MONETARY` do `en-GB` i `LC_TIME` do `es-ES`:

```C
_wsetlocale(LC_ALL, L"de-DE");
_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja biblioteki środowiska uruchomieniowego języka C](../c-runtime-library/c-run-time-library-reference.md)  
[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)  
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)  
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)  
[Ciągi języka](../c-runtime-library/language-strings.md)  
[Ciągi Kraj/Region](../c-runtime-library/country-region-strings.md)  