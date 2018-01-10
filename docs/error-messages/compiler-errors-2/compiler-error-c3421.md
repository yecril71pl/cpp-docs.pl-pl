---
title: "C3421 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3421
dev_langs: C++
helpviewer_keywords: C3421
ms.assetid: b52050c6-17a4-424a-8894-337b0cec7010
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b702bd6481041599c8ed67cf5f7e2443864bf0a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3421"></a>C3421 błąd kompilatora
'type': nie można wywołać finalizatora dla tej klasy, ponieważ jest on niedostępny lub nie istnieje  
  
 Finalizator jest niejawnie prywatne, więc nie można wywołać z poza jego typ otaczający.  
  
 Aby uzyskać więcej informacji, zobacz [destruktory i finalizatory w porady: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3421.  
  
```  
// C3421.cpp  
// compile with: /clr  
ref class A {};  
  
ref class B {   
   !B() {}  
  
public:  
   ~B() {}  
};  
  
int main() {  
   A a;  
   a.!A();   // C3421  
  
   B b;  
   b.!B();   // C3421  
}  
```