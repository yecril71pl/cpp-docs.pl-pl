---
title: Kompilatora (poziom 1) ostrzeżenie C4674 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4674
dev_langs:
- C++
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ede4ac8f8d0af94d998914b8a434cd8b2a9f482
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279782"
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
