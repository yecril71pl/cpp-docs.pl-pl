---
title: Kompilatora (poziom 2) ostrzeżenie C4396 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4396
dev_langs:
- C++
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b937b6ecebedc6984279502a5f64b287f09bd2d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290673"
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