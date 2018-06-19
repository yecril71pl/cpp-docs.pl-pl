---
title: Kompilatora (poziom 1) ostrzeżenie C4488 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4488
dev_langs:
- C++
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a3c5fc64637d989066acfa90715c50504664231
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281525"
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