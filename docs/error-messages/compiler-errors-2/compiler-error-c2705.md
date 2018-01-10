---
title: "C2705 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2705
dev_langs: C++
helpviewer_keywords: C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4aa9cb8574675763b9e51e0409b61dc09e3ab810
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2705"></a>C2705 błąd kompilatora
"etykieta": niedozwolony skok do zakresu "bloku obsługi wyjątków"  
  
 Wykonanie przechodzi do etykiety w `try` / `catch`, `__try` / `__except`, `__try` / `__finally` bloku. Aby uzyskać więcej informacji, zobacz [obsługi wyjątków](../../cpp/exception-handling-in-visual-cpp.md).  
  
 Poniższy przykład generuje C2705:  
  
```  
// C2705.cpp  
int main() {  
goto trouble;  
   __try {  
      trouble: ;   // C2705  
   }  
   __finally {}  
  
   // try the following line instead  
   // trouble: ;  
}  
```