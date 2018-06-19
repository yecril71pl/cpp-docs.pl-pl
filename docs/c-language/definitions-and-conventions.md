---
title: Definicje i konwencje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- nonterminals definition
ms.assetid: f9b3cf5f-6a7c-4a10-9b18-9d4a43efdaeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99f227f37f4a9de92f244df5988f7ee8088e41d5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384149"
---
# <a name="definitions-and-conventions"></a>Definicje i konwencje
Terminale są punkty końcowe w definicji składni. Możliwe jest inne rozwiązanie. Terminale obejmują zestaw zawiera wyrazy zastrzeżone i identyfikatory zdefiniowane przez użytkownika.  
  
 Symboli nieterminalnych symboli zastępczych w składni i zdefiniowany w innym miejscu w tej składni podsumowania. Definicje może mieć wartość recursive.  
  
 Opcjonalny składnik jest oznaczany jako opcjonalnych. Na przykład  
  
```  
  
{  
expression <SUB>opt</SUB> }  
```  
  
 Określa opcjonalne wyrażenie ujęte w nawiasy klamrowe.  
  
 Konwencje składni używane są atrybuty czcionkę dla różnych składników składni. Symbole i czcionek są następujące:  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|*nonterminal*|Kursywą wskazuje symboli nieterminalnych.|  
|**const**|Terminale czcionką pogrubioną są literału wyrazy zastrzeżone i symboli, które należy wprowadzić, jak pokazano. Znaki w tym kontekście zawsze jest uwzględniana wielkość liter.|  
|OPT|Opt symboli nieterminalnych następuje zawsze są opcjonalne.|  
|domyślne krój czcionki|Znaki w zestawie opisane lub wymienione w tej czcionce mogą być używane jako terminali w instrukcjach języka C.|  
  
 Dwukropkiem (**:**) po nonterminal wprowadza jego definicji. Alternatywne definicje są wymienione w osobnych wierszach, z wyjątkiem gdy poprzedzone znakiem wyrazy "jedna z."  
  
## <a name="see-also"></a>Zobacz też  
 [Podsumowanie dotyczące składni języka C](../c-language/c-language-syntax-summary.md)