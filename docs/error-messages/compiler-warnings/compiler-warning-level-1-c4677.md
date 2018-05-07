---
title: Kompilatora (poziom 1) ostrzeżenie C4677 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4677
dev_langs:
- C++
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3511ad3100bf695cec5df97703b39e5926c71c11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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