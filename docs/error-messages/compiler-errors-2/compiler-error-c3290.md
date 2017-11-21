---
title: "C3290 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3290
dev_langs: C++
helpviewer_keywords: C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c3dceac5102936bbb86f5c103fb0c9240f5ee2d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3290"></a>C3290 błąd kompilatora
'type': właściwość prosta nie może mieć typu referencyjnego  
  
 Właściwość została niepoprawnie zadeklarowany. Gdy zadeklarować właściwość prosta, kompilator tworzy zmienną, która spowoduje zaktualizowanie właściwości i nie jest możliwe odwołaniem śledzącym zmiennej w klasie.  
  
 Zobacz [właściwości](../../windows/property-cpp-component-extensions.md) i [Operator odwołania śledzenia](../../windows/tracking-reference-operator-cpp-component-extensions.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3290.  
  
```  
// C3290.cpp  
// compile with: /clr /c  
ref struct R {};  
  
ref struct X {  
   R^ mr;  
  
   property R % y;   // C3290  
   property R ^ x;   // OK  
  
   // OK  
   property R% prop {  
      R% get() {   
         return *mr;   
      }  
  
      void set(R%) {}  
   }  
};  
  
int main() {  
   X x;  
   R% xp = x.prop;  
}  
```