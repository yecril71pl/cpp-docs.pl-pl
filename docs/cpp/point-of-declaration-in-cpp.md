---
title: "Punkt deklaracji w języku C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64c1fa1d6d8feb4b869957101bb4b37f125d0f8b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="point-of-declaration-in-c"></a>Punkt deklaracji w kodzie C++
Nazwa jest uważana za zgłaszane, natychmiast po jej deklarator, ale przed jego Inicjator (opcjonalnie). (Aby uzyskać więcej informacji o deklaratorów, zobacz [deklaracje i definicje](declarations-and-definitions-cpp.md).)  
  
 Rozważmy następujący przykład:  
  
```  
// point_of_declaration1.cpp  
// compile with: /W1   
double dVar = 7.0;  
int main()  
{  
   double dVar = dVar;   // C4700  
}  
```  
  
 Jeśli punkt deklaracji zostały *po* inicjowania, a następnie lokalnej `dVar` będzie można zainicjować 7.0, wartość zmiennej globalnej `dVar`. Jednakże, ponieważ nie jest przypadek, `dVar` niezdefiniowana wartość została zainicjowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Zakres](../cpp/scope-visual-cpp.md)