---
title: Ustawienia regionalne i strony kodowe | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- locales [C++], about locales
- locale IDs [C++]
- locales [C++]
- code pages [C++]
- code pages [C++], dynamically changing
- character sets [C++], code pages
- multibyte code pages [C++]
- character sets [C++], locales
- localization [C++], code pages
- localization [C++], locales
- code pages [C++], locales
- conventions [C++], international character support
ms.assetid: bd937361-b6d3-4c98-af95-beb7c903187b
caps.latest.revision: "9"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 1115af5eb7726138a1954f832ec2761a47667e44
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="locales-and-code-pages"></a>Ustawienia regionalne i strony kodowe
Identyfikator ustawień regionalnych odzwierciedla konwencje lokalnych i język dla określonego regionu geograficznego. Danego języka może być używany w więcej niż jeden kraj/region; na przykład portugalski jest używany w Brazylia także jak Portugalii. Z drugiej strony kraj/region może mieć więcej niż jednym języku. Na przykład Kanada ma dwa języki: angielski i francuski. W związku z tym Kanada ma dwa różne ustawienia regionalne: kanadyjskich w języku angielskim i francuskim kanadyjskich. Niektóre kategorie zależne od ustawień regionalnych obejmują formatowanie dat i format wyświetlania wartości pieniężnych.  
  
 Język określa tekstu i formatowanie konwencje, gdy kraj/region sprawdza lokalne konwencje danych. Każdy języka znajduje się unikatowy mapowanie, reprezentowany przez stron kodowych zawierającej znaki spoza alfabetu (np. znaki interpunkcyjne i cyfry). Strona kodowa jest zestawem znaków i jest związane z językiem. W efekcie [ustawień regionalnych](../c-runtime-library/locale.md) to unikatowe połączenie języka, kraju/regionu i strony kodowej. Można zmienić ustawienia strony ustawień regionalnych i kodu w czasie wykonywania przez wywołanie metody [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) funkcji.  
  
 W różnych językach może używać innej strony kodowe. Na przykład stronę kodową ANSI 1252 jest używana w języku angielskim i większość języków europejskich i stronę kodową ANSI 932 służy do japoński Kanji. Prawie wszystkie strony kodowe udostępnianie zestaw znaków ASCII dla najniższej 128 znaków (0x00 0x7F).  
  
 Wszystkie strony kodowej jednobajtowe może być reprezentowana w tabeli (z wpisów 256) jako mapowanie wartości bajtu znaków (łącznie z cyfr i znaków interpunkcyjnych) lub symboli. Wszystkie strony kodowe wielobajtowe również może być reprezentowany jako tabelę bardzo duże (zapisami 64 KB) wartości znaków dwubajtowych. W praktyce jednak ją są zazwyczaj reprezentowany jako tabelę dla najpierw 256 znaków (jednobajtowe), a zakresy dla wartości znaków dwubajtowych.  
  
 Aby uzyskać więcej informacji na temat stron kodowych, zobacz [stron kodowych](../c-runtime-library/code-pages.md).  
  
 Biblioteki wykonawcze języka C występują dwa typy stron kodowych wewnętrzny: ustawienia regionalne i wielobajtowe. Bieżąca strona kodowa można zmienić podczas wykonywania programu (zobacz dokumentację [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) i [_setmbcp —](../c-runtime-library/reference/setmbcp.md) funkcji). Biblioteki wykonawczej mogą również uzyskać i użyj wartości strony kodowej systemu operacyjnego. W systemie Windows 2000 strona kodowa systemu operacyjnego jest strona kodowa "ANSI domyślne systemu". Ta strona kodowa jest stały czas wykonywania programu.  
  
 Strona kodowa ustawień lokalnych zmiany, zachowanie zestawu zależnego od ustawień regionalnych zmiany funkcji w tym definiowane za pomocą stron kodowych wybrany. Domyślnie wszystkie funkcje zależne od ustawień regionalnych rozpocząć wykonywanie strona kodowa ustawień lokalnych unikatowe dla ustawień regionalnych "C". Strona kodowa ustawień regionalnych wewnętrzny (a także inne właściwości specyficzne dla ustawień regionalnych) można zmienić wywołując `setlocale` funkcji. Wywołanie `setlocale`(lc_all —, "") ustawia ustawienia regionalne do wskazanej przez użytkownika ustawień regionalnych systemu operacyjnego.  
  
 Podobnie strony kodowe wielobajtowe zmiany, zachowanie zmiany wielobajtowe funkcji, który definiowane za pomocą stron kodowych wybrany. Domyślnie wszystkie funkcje wielobajtowe rozpocząć wykonywania za pomocą strony kodowe wielobajtowe odpowiadający domyślna strona kodowa systemu operacyjnego. Strony kodowe wielobajtowe wewnętrzny można zmienić, wywołując `_setmbcp` funkcji.  
  
 Funkcja wykonawcze języka C `setlocale` ustawia zmiany i wysyła zapytanie do niektórych lub wszystkich informacji o ustawieniach regionalnych bieżącego programu. [_Wsetlocale —](../c-runtime-library/reference/setlocale-wsetlocale.md) procedura jest wersja znaków dwubajtowych `setlocale`; argumentów i wartości zwracanych z `_wsetlocale` są ciągami znaków dwubajtowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Unicode i MBCS](../text/unicode-and-mbcs.md)   
 [Zalety znak przenośności zestawu](../text/benefits-of-character-set-portability.md)