---
title: "C3628 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3628
dev_langs: C++
helpviewer_keywords: C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 131b2829991d0d8c40b64c903afd45b485b9ba55
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3628"></a>C3628 błąd kompilatora
"klasa podstawowa": zarządzane lub WinRTclasses obsługują tylko publiczne dziedziczenie  
  
Podjęto próbę użycia zarządzanego lub WinRT klasy [prywatnej](../../cpp/private-cpp.md) lub [chronione](../../cpp/protected-cpp.md) klasy podstawowej. A zarządzane lub WinRT klasy można użyć tylko jako klasy podstawowej z [publicznego](../../cpp/public-cpp.md) dostępu.  
  
Poniższy przykład generuje C3628 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C3628a.cpp  
// compile with: /clr  
ref class B {  
};  
  
ref class D : private B {   // C3628  
  
// The following line resolves the error.  
// ref class D : public B {  
};  
  
int main() {  
}  
```  
