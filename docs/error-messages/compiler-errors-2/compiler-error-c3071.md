---
title: "C3071 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3071
dev_langs: C++
helpviewer_keywords: C3071
ms.assetid: 69879e66-a60e-4058-9bbd-d5c5e2d8ee37
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fc5cca3bdb0ff10f9f11c89ed3193002ebc884b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3071"></a>C3071 błąd kompilatora
operator "operator" można stosować do wystąpienia klasy ref lub typu wartościowego  
  
 Nie można używać operatora CLR na typ macierzysty. Operator może służyć w klasie ref lub ref struct (typ wartości), ale nie: Typ macierzysty takich jak int lub alias dla typu macierzystego, takich jak System::Int32. Te typy nie można spakować z kodu C++ w taki sposób, który odwołuje się do zmiennej macierzystego, więc nie można używać operatora.  
  
 Aby uzyskać więcej informacji, zobacz [Operator odwołania śledzenia](../../windows/tracking-reference-operator-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3071.  
  
```  
// C3071.cpp  
// compile with: /clr  
class N {};  
ref struct R {};  
  
int main() {  
   N n;  
   %n;   // C3071  
  
   R r;  
   R ^ r2 = %r;   // OK  
}  
```