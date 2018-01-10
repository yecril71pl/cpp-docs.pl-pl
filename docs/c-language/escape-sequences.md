---
title: Sekwencje specjalne | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- "\r escape sequence"
- double backslash
- horizontal-tab 	 escape sequence
- (') single quotation mark
- "bell character \a escape sequence"
- escape sequences
- hexadecimal escape sequence
- carriage returns
- tab 	 escape sequence
- "\f escape sequence"
- quotation marks, single
- "formfeed \f escape sequence"
- "\v escape sequence"
- control character escape sequences
- " symbol in escape sequences"
- octal escape sequence
- escape characters
- "newline character \n escape sequence"
- nongraphic control characters
- question mark, literal
- "\nescape sequence"
- "vertical tab \v escape sequence"
- "\a escape sequence"
- '? symbol'
- '? symbol, escape sequence character'
- "	 escape sequence"
- backspace escape sequence
ms.assetid: 5aef377f-a76c-4d5c-aa04-8308758ad6a8
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d341aa5af2b16d1a29bc4e3dfe2f97a68b73d6ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="escape-sequences"></a>Sekwencje unikowe
Znak kombinacji składające się z od ukośnika odwrotnego (**\\**) następują litery lub przy użyciu kombinacji cyfr są nazywane "sekwencje specjalne". Aby przedstawić znaku nowego wiersza, pojedynczego cudzysłowu lub niektórych innych znaków w stałej znakowej, należy użyć sekwencji unikowych. Sekwencja specjalna jest traktowany jako pojedynczy znak i dlatego jest nieprawidłowe w stałej znakowej.  
  
 Sekwencje unikowe są zwykle używane do określ akcje, takie jak znaki powrotu karetki i karcie przemieszczania na terminale i drukarek. Są również używane zapewnienie reprezentacje literału i znaki niedrukowalne znaki, które zwykle mają specjalne znaczenie, takich jak podwójny cudzysłów (**"**). W poniższej tabeli wymieniono sekwencji unikowych ANSI i ich znaczenie.  
  
 Należy pamiętać, że poprzedzone znakiem zapytania ukośnik odwrotny (**\\?**) określa literału znaku zapytania w przypadkach, w którym sekwencja znaków może zostać błędnie zinterpretowane jako — trigram. Zobacz [Trigramów](../c-language/trigraphs.md) Aby uzyskać więcej informacji.  
  
### <a name="escape-sequences"></a>Sekwencje unikowe  
  
|Sekwencja unikowa|Reprezentuje|  
|---------------------|----------------|  
|**\a**|Dzwonka (alert)|  
|**\b**|Backspace|  
|**\f**|Wysuw strony|  
|**\n**|Nowy wiersz|  
|**\r**|Powrót karetki|  
|**\t**|Tabulator poziomy|  
|**\v**|Tabulator pionowy|  
|**\\'**|Znak pojedynczego cudzysłowu|  
|**\\"**|Podwójny cudzysłów|  
|**\\\\**|ukośnik odwrotny|  
|**\\?**|Literał znaku zapytania|  
|**\\***ooo*|Znaków ASCII w notacji ósemkowe|  
|**\x** *hh*|Znaków ASCII w formacie szesnastkowym|  
|**\x** *gg*|Znak Unicode w systemie szesnastkowym, jeśli ta sekwencja ucieczki jest używana w szerokich znaków stała ani literał ciągu Unicode.<br /><br /> Na przykład `WCHAR f = L'\x4e00'` lub `WCHAR b[] = L"The Chinese character for one is \x4e00"`.|  
  
 **Dotyczące firmy Microsoft**  
  
 Jeśli ukośnik odwrotny poprzedza znak, który nie ma w tabeli, kompilator obsługuje Niezdefiniowany znak jako sam znak. Na przykład `\c` jest traktowany jako `c`.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Sekwencje unikowe umożliwiają wysyłanie Niegraficzne znaki kontrolne na urządzeniu. Na przykład znak ESC (**\033**) jest często używany jako pierwszy znak polecenia sterowania do terminal lub drukarki. Niektóre sekwencji unikowych są specyficzne dla urządzenia. Na przykład karta pionowego i wysuwu strony sekwencje specjalne (**\v** i **\f**) nie ma wpływu na dane wyjściowe ekranu, ale wykonują operacje odpowiednich drukarek.  
  
 Można również użyć kreska ułamkowa odwrócona (**\\**) jako znak kontynuacji. Gdy nowym wierszem znaków (odpowiednik naciśnięcie klawisza RETURN) od razu następuje ukośnik odwrotny, kompilator ignoruje ukośniku odwrotnym i znakiem nowego wiersza i traktuje następnego wiersza w ramach poprzedniego wiersza. Jest to przydatne, przede wszystkim dotyczące definicje preprocesora więcej niż jeden wiersz. Na przykład:  
  
```  
#define assert(exp) \  
( (exp) ? (void) 0:_assert( #exp, __FILE__, __LINE__ ) )  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe znakowe języka C](../c-language/c-character-constants.md)