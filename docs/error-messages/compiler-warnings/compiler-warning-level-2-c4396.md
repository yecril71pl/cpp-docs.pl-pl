---
title: "Kompilatora (poziom 2) ostrzeżenie C4396 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4396
dev_langs: C++
helpviewer_keywords: C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bd40c2b78c12cff4b3904348c86dff1c7c3da0b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-2-c4396"></a>Kompilator C4396 ostrzegawcze (poziom 2)
"Nazwa": wbudowany specyfikator nie można użyć, gdy zaprzyjaźniona deklaracja odnosi się do specjalizacji szablonu funkcji  
  
 Specjalizacja szablonu funkcji nie można określić dowolną z [wbudowanego](../../cpp/inline-functions-cpp.md) specyfikatory. Kompilator generuje ostrzeżenie C4396 i ignoruje wbudowany specyfikator.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń `inline`, `__inline`, lub `__forceinline` specyfikator w deklaracji funkcji friend.  
  
## <a name="example"></a>Przykład  
 Nieprawidłowy friend deklaracji z funkcji ilustruje poniższy przykład kodu `inline` specyfikator.  
  
```  
// C4396.cpp  
// compile with: /W2 /c  
  
class X;   
template<class T> void Func(T t, int i);  
  
class X {  
    friend inline void Func<char>(char t, int i);  //C4396  
// try the following line instead  
//    friend void Func<char>(char t, int i);   
    int i;  
};  
```