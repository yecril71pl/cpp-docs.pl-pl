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
ms.openlocfilehash: fef56154f34f645b279ffccd99915d366388cb06
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026705"
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
  
Jawne konwersje typów całkowitych są niedozwolone w wyrażeniach stałych innych typów i typów pochodnych są niedozwolone z wyjątkiem sytuacji, gdy używana jako argumenty do `sizeof` operatora.  
  
Nie można użyć operatora przecinka i operatory przypisania w wyrażeniach stałych.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy wyrażeń](../cpp/types-of-expressions.md)