---
title: "C3255 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3255
dev_langs: C++
helpviewer_keywords: C3255
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 86052e8ffa7e9ba9627a290318dbe6115af3d36c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3255"></a>C3255 błąd kompilatora
"wartość typu": nie można dynamicznie przydzielić tego obiektu typu wartościowego na natywnej stercie  
  
 Wystąpienia typu wartości (zobacz [klas i struktur](../../windows/classes-and-structs-cpp-component-extensions.md)) zawierających zarządzanych członków można tworzyć na stosie, ale nie na stosie.  
  
 Poniższy przykład generuje C3255:  
  
```  
// C3255.cpp  
// compile with: /clr  
using namespace System;  
value struct V {  
   Object^ o;  
};  
  
value struct V2 {  
   int i;  
};  
  
int main() {  
   V* pv = new V;   // C3255  
   V2* pv2 = new V2;  
   V v2;  
}  
```  
