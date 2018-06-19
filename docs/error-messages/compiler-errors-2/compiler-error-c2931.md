---
title: C2931 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2931
dev_langs:
- C++
helpviewer_keywords:
- C2931
ms.assetid: 33430407-b149-4ba3-baf8-b0dae1ea3a5d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e5dd8db3d39ff8aec2084736483c4d325d81314
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246973"
---
# <a name="compiler-error-c2931"></a>C2931 błąd kompilatora
"class": typ klasy identyfikator ponownie zdefiniować jako funkcję elementu członkowskiego 'Identyfikator'  
  
 Klasy ogólne lub szablonu nie można użyć jako funkcję elementu członkowskiego z innej klasy.  
  
 Ten błąd może być spowodowany nieprawidłowo są dopasowywane w nawiasach klamrowych.  
  
 Poniższy przykład generuje C2931:  
  
```  
// C2931.cpp  
// compile with: /c  
template<class T>   
struct TC { };   
struct MyStruct {  
   void TC<int>();   // C2931  
};  
  
struct TC2 { };   
struct MyStruct2 {  
   void TC2();  
};  
```  
  
 C2931 może również wystąpić, gdy użycie typów ogólnych:  
  
```  
// C2931b.cpp  
// compile with: /clr /c  
generic<class T> ref struct GC {};  
struct MyStruct {  
   void GC<int>();   // C2931  
   void GC2();   // OK  
};  
```