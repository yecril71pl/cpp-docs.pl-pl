---
title: "C3766 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3766
dev_langs: C++
helpviewer_keywords: C3766
ms.assetid: b5af2089-2e1e-4e45-a41d-495b6c55656e
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f6df0cd4fea3f1f4b4e5e744b210fcc62bfff5f5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3766"></a>C3766 błąd kompilatora
'type' musi dostarczyć implementację interfejsu "function" — Metoda  
  
 Klasa, która dziedziczy po interfejsie musi implementować członków interfejsu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3766.  
  
```  
// C3766.cpp  
// compile with: /clr /c  
  
delegate void MyDel();  
  
interface struct IFace {  
   virtual event MyDel ^ E;  
};  
  
ref struct Class1 : public IFace {};   // C3766  
  
// OK  
ref struct Class2 : public IFace {  
   virtual event MyDel ^ E {  
      void add(MyDel ^) {}  
      void remove(MyDel ^) {}  
   }  
};  
```