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
ms.openlocfilehash: 74a29acfcdc58b068ebabe9bc1c9b033cf801c21
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760409"
---
# <a name="definitions-and-conventions"></a>Definicje i konwencje
Terminale to punkty końcowe w definicji składni. Możliwe jest inne rozwiązanie. Terminale obejmują zbiór słów zastrzeżonych oraz identyfikatorów zdefiniowanych przez użytkownika.  
  
Symboli nieterminalnych są symbole zastępcze w składni i są definiowane w innych miejscach w tej składni podsumowania. Definicje mogą być cykliczne.  
  
Opcjonalny składnik jest wskazywany przez indeksem <sub>zoptymalizowany pod kątem</sub>. Na przykład  
  
> **{** *wyrażenie*<sub>zoptymalizowany pod kątem</sub> **}**
  
Określa opcjonalne wyrażenie ujęte w nawiasy klamrowe.  
  
Konwencje składni Użyj atrybutów czcionkę dla różnych składników składni. Symbole i czcionki są następujące:  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|*nieterminalnych*|Kursywa wskazuje symboli nieterminalnych.|  
|**const**|Terminale czcionką pogrubioną są literału wyrazy zastrzeżone i symboli, które należy wprowadzić, jak pokazano. Znaki w tym kontekście są zawsze z uwzględnieniem wielkości liter.|  
|<sub>opt</sub>|Następuje symboli nieterminalnych <sub>zoptymalizowany pod kątem</sub> zawsze są opcjonalne.|  
|krój czcionki domyślnej|Znaków w zestawie opisane lub wymienionych w tej czcionce może służyć jako terminale w instrukcjach języka C.|  
  
Dwukropek (**:**) po nieterminalnych wprowadza jego definicji. Alternatywne definicje są wymienione w osobnych wierszach, z wyjątkiem, gdy poprzedzone znakiem słowa "poszczególnych."  
  
## <a name="see-also"></a>Zobacz też  
[Podsumowanie dotyczące składni języka C](../c-language/c-language-syntax-summary.md)