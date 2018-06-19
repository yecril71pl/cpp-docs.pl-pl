---
title: C3290 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3290
dev_langs:
- C++
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf65a35469ca978b0464c6f7275a6ac0e331da5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256386"
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