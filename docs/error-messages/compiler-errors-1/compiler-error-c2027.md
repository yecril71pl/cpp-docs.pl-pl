---
title: C2027 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2027
dev_langs:
- C++
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be3c85d2ffbd3fffe4e1e6ce6dafc615f199c00a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167447"
---
# <a name="compiler-error-c2027"></a>C2027 błąd kompilatora
Użycie niezdefiniowanego typu "type"  
  
 Nie można użyć typu, dopóki nie jest zdefiniowana. Aby rozwiązać problem, upewnij się, że typ jest w pełni zdefiniowana przed odwołuje.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2027.  
  
```  
// C2027.cpp  
class C;  
class D {  
public:  
   void func() {  
   }  
};  
  
int main() {  
   C *pC;  
   pC->func();   // C2027  
  
   D *pD;  
   pD->func();  
}  
```  
  
## <a name="example"></a>Przykład  
 Istnieje możliwość zadeklarować wskaźnika do typu zadeklarowana ale niezdefiniowana.  Ale Visual C++ nie zezwala na odwołanie do niezdefiniowanego typu.  
  
 Poniższy przykład generuje C2027.  
  
```  
// C2027_b.cpp  
class A;  
A& CreateA();  
  
class B;  
B* CreateB();  
  
int main() {  
   CreateA();   // C2027  
   CreateB();   // OK  
}  
```