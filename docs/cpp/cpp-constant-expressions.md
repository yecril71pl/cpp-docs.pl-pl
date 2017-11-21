---
title: "Wyrażenia stałe języka C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9f6961e210af254cd807b133e034610f03ca866e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-constant-expressions"></a>Wyrażenia stałe języka C++
A *stałej* wartość to taki, który nie ulega zmianie. C++ zawiera dwa słowa kluczowe umożliwia express zamiar obiektu nie jest przeznaczona do zmodyfikowania oraz do wymuszania tego celem.  
  
 Wyrażenia stałe wymaga C++ — wyrażeń, które oszacowane jako stała — dla deklaracji:  
  
-   Granice tablicy  
  
-   Selektory w instrukcji case  
  
-   Specyfikacja długość pola bitowego  
  
-   Inicjatory — wyliczenie  
  
 Tylko argumentów operacji, które są w wyrażenia stałe są:  
  
-   Literały  
  
-   Stałe — wyliczenie  
  
-   Wartości zadeklarować jako const, które są inicjowane z wyrażenia stałe  
  
-   `sizeof`wyrażenia  
  
 Stałe nonintegral muszą zostać skonwertowane (jawnie lub niejawnie) do typów całkowitych pod kątem legalności zastosowania w wyrażeniu stałym. W związku z tym następujący kod jest prawnych:  
  
```  
const double Size = 11.0;  
char chArray[(int)Size];  
```  
  
 Jawne konwersje typów całkowitych są w wyrażenia stałe; wszystkie inne typy i typów pochodnych są niedozwolone, z wyjątkiem przypadków, gdy używane jako argumenty do `sizeof` operatora.  
  
 Nie można użyć przecinka i operatory przypisania w wyrażenia stałe.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy wyrażeń](../cpp/types-of-expressions.md)