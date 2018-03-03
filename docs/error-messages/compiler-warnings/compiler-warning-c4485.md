---
title: "C4485 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4485
dev_langs:
- C++
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1289ee1ce2a5f756d7a21f966424007eee704ac1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4485"></a>C4485 ostrzeżenia kompilatora
"override_function": pasuje do metody podstawowej klasy referencyjnej "base_class_function", ale nie jest oznaczony jako "new" lub "override"; Założono "new" (i "virtual")  
  
 Zastępuje metodę dostępu, bez `virtual` — słowo kluczowe — funkcja dostępu klasy podstawowej, ale `override` lub `new` specyfikator nie jest częścią elementu zastępowanie podpisu funkcji. Dodaj `new` lub `override` specyfikator rozwiązywać to ostrzeżenie.  
  
 Zobacz [zastąpienia](../../windows/override-cpp-component-extensions.md) i [new (nowe gniazdo w vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md) Aby uzyskać więcej informacji.  
  
 C4485 jest zawsze wystawione jako błąd. Użyj [ostrzeżenie](../../preprocessor/warning.md) pragma do pomijania C4485.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4485  
  
```  
// C4485.cpp  
// compile with: /clr  
delegate void Del();  
  
ref struct A {  
   virtual event Del ^E;  
};  
  
ref struct B : A {  
   virtual event Del ^E;   // C4485  
};  
  
ref struct C : B {  
   virtual event Del ^E {  
      void raise() override {}  
      void add(Del ^) override {}  
      void remove(Del^) override {}  
   }  
};  
```