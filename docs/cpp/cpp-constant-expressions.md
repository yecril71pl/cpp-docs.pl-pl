---
title: Wyrażenia stałe języka C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06a07c9d37994b4214da9b2eb53d02104525d7c4
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408115"
---
# <a name="c-constant-expressions"></a>Wyrażenia stałe języka C++
A *stałej* wartość to taki, który nie powoduje zmiany. C++ zawiera dwa słowa kluczowe umożliwiające express celem obiektu nie jest przeznaczony do modyfikacji i wymusić tym przeznaczeniem.  
  
C++ wymaga wyrażenia stałe — wyrażeń, które oszacowane jako stała — dla deklaracji:  
  
 -   Granice tablicy  
      
 -   Selektory w instrukcji case  
      
 -   Specyfikacja długości pole bitowe  
      
 -   Inicjatory wyliczenia  
  
Tylko argumentów operacji, które są dopuszczalne w wyrażenia stałe są następujące:  
  
 -   Literały  
      
 -   Stałe wyliczeń  
      
 -   Jako const zadeklarowane jako wartości, które są inicjowane przy użyciu wyrażeń stałych  
      
 -   **Operator sizeof** wyrażeń  
  
Stałe nonintegral muszą zostać przekonwertowane (jawnie lub niejawnie) typów całkowitych pod kątem w wyrażeniu stałym. W związku z tym poniższy kod jest dozwolony:  
  
```cpp 
const double Size = 11.0;  
char chArray[(int)Size];  
```  
  
Jawne konwersje typów całkowitych są niedozwolone w wyrażeniach stałych innych typów i typów pochodnych są niedozwolone z wyjątkiem sytuacji, gdy używana jako argumenty do **sizeof** operatora.  
  
Nie można użyć operatora przecinka i operatory przypisania w wyrażeniach stałych.  
  
## <a name="see-also"></a>Zobacz także  
 [Typy wyrażeń](../cpp/types-of-expressions.md)