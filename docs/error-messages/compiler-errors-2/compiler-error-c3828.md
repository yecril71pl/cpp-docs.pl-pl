---
title: "C3828 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3828
dev_langs: C++
helpviewer_keywords: C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1b2dfaa6e0c414c80122bcb4291bb021bc1f3c74
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3828"></a>C3828 błąd kompilatora
"typu obiektu": argumenty umieszczania są niedozwolone podczas tworzenia wystąpienia zarządzane lub WinRTclasses  
  
 Podczas tworzenia obiektu typu zarządzanego lub typu środowiska wykonawczego systemu Windows, nie można użyć formularza umieszczania operatora [ref new, gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md) lub [nowe](../../cpp/new-operator-cpp.md).  
  
 Poniższy przykład generuje C3828 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C3828a.cpp  
// compile with: /clr  
ref struct M {  
};  
  
ref struct N {  
   static array<char>^ bytes = gcnew array<char>(256);  
};  
  
int main() {  
   M ^m1 = new (&N::bytes) M();   // C3828  
   // The following line fixes the error.  
   // M ^m1 = gcnew M();  
}  
```