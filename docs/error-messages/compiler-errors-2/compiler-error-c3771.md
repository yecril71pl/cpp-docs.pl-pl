---
title: "C3771 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3771
dev_langs: C++
helpviewer_keywords: C3771
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dc3e9639fa83524e797c22edd771c847046f0e3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3771"></a>C3771 błąd kompilatora
"identyfikator": deklaracja friend nie można odnaleźć w najbliższym zakresie przestrzeni nazw  
  
Deklaracja szablonu klasy dla określonego szablonu *identyfikator* nie można odnaleźć w bieżącym obszarze nazw.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że deklaracji szablonu klasy dla identyfikatora szablonu jest zdefiniowana w bieżącej przestrzeni nazw lub że identyfikator szablonu jest w pełni kwalifikowaną nazwę.  
  
## <a name="example"></a>Przykład  
Poniższy przykładowy kod deklaruje szablon klasy i funkcji w przestrzeni nazw `NA`, ale próbuje zadeklarować friend szablonu funkcji w przestrzeni nazw `NB`.  
  
```cpp  
// C3771.cpp   
// compile with: /c  
  
namespace NA {  
template<class T> class A {  
    void aFunction(T t) {};  
    };  
}  
// using namespace NA;  
namespace NB {  
    class X {  
        template<class T> friend void A<T>::aFunction(T); // C3771  
// try the following line instead  
//      template<class T> friend void NA::A<T>::aFunction(T);  
// or try "using namespace NA;" instead.  
    };  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
[Szablony](../../cpp/templates-cpp.md)  