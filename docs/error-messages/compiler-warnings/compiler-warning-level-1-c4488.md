---
title: "Kompilatora (poziom 1) ostrzeżenie C4488 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4488
dev_langs:
- C++
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ad82e9dc85d818aacd78aaeb287777bd91927a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4488"></a>Kompilator C4488 ostrzegawcze (poziom 1)
"Funkcja": wymaga słowa kluczowego "— słowo kluczowe" implementuje metody interfejsu "interface_method"  
  
 Klasa musi implementować wszystkie elementy członkowskie interfejsu, po którym bezpośrednio dziedziczy. Zaimplementowany element musi mieć publiczny dostępność i musi być oznaczona jako wirtualna.  
  
## <a name="example"></a>Przykład  
 C4488 może być zaimplementowany element członkowski nie jest publiczny. Poniższy przykład generuje C4488.  
  
```  
// C4488.cpp  
// compile with: /clr /c /W1 /WX  
interface struct MyI {  
   void f1();  
};  
  
// implemented member not public  
ref class B : MyI { virtual void f1() {} };  // C4488  
  
// OK  
ref class C : MyI {  
public:  
   virtual void f1() {}  
};  
```  
  
## <a name="example"></a>Przykład  
 C4488 może być zaimplementowany element członkowski nie jest oznaczona jako wirtualna. Poniższy przykład generuje C4488.  
  
```  
// C4488_b.cpp  
// compile with: /clr /c /W1 /WX  
interface struct MyI {  
   void f1();  
};  
  
ref struct B : MyI { void f1() {} };   // C4488  
ref struct C : MyI { virtual void f1() {} };   // OK  
```