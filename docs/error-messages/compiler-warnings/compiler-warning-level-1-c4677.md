---
title: "Kompilatora (poziom 1) ostrzeżenie C4677 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4677
dev_langs: C++
helpviewer_keywords: C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a597fa2373de1a2650a86c0b8d4f51bad35d9818
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4677"></a>Kompilator C4677 ostrzegawcze (poziom 1)
"Funkcja": podpis elementu z systemem innym niż nieprywatnego elementu członkowskiego zawiera prywatny typ zestawu "private_type"  
  
 Typ, który ma powszechnej dostępności poza zestaw używa typu, który ma dostęp prywatnej poza zestaw. Składnik, który odwołuje się do typu publicznego zestawu nie będzie mógł używać elementu członkowskiego typu lub elementy członkowskie, które odwołują się prywatny typ zestawu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4677.  
  
```  
// C4677.cpp  
// compile with: /clr /c /W1  
delegate void TestDel();  
public delegate void TestDel2();  
  
public ref class MyClass {  
public:  
   static event TestDel^ MyClass_Event;   // C4677  
   static event TestDel2^ MyClass_Event2;   // OK  
};  
```