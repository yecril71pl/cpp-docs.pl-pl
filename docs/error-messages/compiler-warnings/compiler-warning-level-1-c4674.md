---
title: "Kompilatora (poziom 1) ostrzeżenie C4674 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4674
dev_langs: C++
helpviewer_keywords: C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3a9776af9dd17c747edb5ca54db197425613673e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4674"></a>Kompilator C4674 ostrzegawcze (poziom 1)
"metoda" powinien być zadeklarowany jako "static" i mieć dokładnie jeden parametr  
  
Podpis operatora konwersja nie jest poprawny. Metoda nie jest uznawane za zdefiniowane przez użytkownika konwersji. Aby uzyskać więcej informacji na temat definiowania operatorów, zobacz [operatory zdefiniowane przez użytkownika (C + +/ CLI)](../../dotnet/user-defined-operators-cpp-cli.md) i [konwersje zdefiniowane przez użytkownika (C + +/ CLI)](../../dotnet/user-defined-conversions-cpp-cli.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4674.  
  
```  
// C4674.cpp  
// compile with: /clr /WX /W1 /LD  
ref class G {  
   int op_Implicit(int i) {   // C4674  
      return 0;  
   }  
};  
```  
