---
title: C3255 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3255
dev_langs:
- C++
helpviewer_keywords:
- C3255
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 740deb9a2981839a12d2570328369daf741a8da9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
