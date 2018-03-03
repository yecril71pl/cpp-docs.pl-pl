---
title: "C4867 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4867
dev_langs:
- C++
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a412080d05e570711fcc65926459f9d2fcc45ed3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4867"></a>C4867 ostrzeżenia kompilatora
"Funkcja": wywołanie funkcji brakuje listy argumentów; Użyj "call", aby utworzyć wskaźnik do elementu członkowskiego  
  
 Wskaźnik do funkcji członkowskiej zainicjowano niepoprawnie.  
  
 To ostrzeżenie można wygenerować wyniku pracy zgodność kompilatora, która została wykonana dla Visual C++ 2005: rozszerzoną zgodność wskaźnika do elementu członkowskiego.  Kod, który skompilowany przed Visual C++ 2005 teraz wygeneruje C4867.  
  
 To zawsze ostrzeżenie jako błąd. Użyj [ostrzeżenie](../../preprocessor/warning.md) pragma, aby wyłączyć to ostrzeżenie. Aby uzyskać więcej informacji na temat C4867 i MFC/ATL, zobacz [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4867.  
  
```  
// C4867.cpp  
// compile with: /c  
class A {  
public:  
   void f(int) {}  
  
   typedef void (A::*TAmtd)(int);  
  
   struct B {  
      TAmtd p;  
   };  
  
   void g() {  
      B b = {f};   // C4867  
      B b2 = {&A::f};   // OK  
   }  
};  
```