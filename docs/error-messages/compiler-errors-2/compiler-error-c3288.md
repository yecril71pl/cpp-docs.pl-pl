---
title: "C3288 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3288
dev_langs: C++
helpviewer_keywords: C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 138afdc77c6631b2699ec645e65032217f9e18d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3288"></a>C3288 błąd kompilatora
"type": niedozwolone anulowanie odwołania do typu uchwytu  
  
 Kompilator Wykryto niedozwolony dereference typu dojścia. Można usunąć odwołania do typu uchwytu i przypisz je do odwołania. Aby uzyskać więcej informacji, zobacz [Operator odwołania śledzenia](../../windows/tracking-reference-operator-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3288.  
  
```  
// C3288.cpp  
// compile with: /clr  
ref class R {};  
int main() {  
   *(System::Object^) nullptr;   // C3288  
  
// OK  
   (System::Object^) nullptr;   // OK  
   R^ r;  
   R% pr = *r;  
}  
```