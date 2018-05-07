---
title: C4485 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4485
dev_langs:
- C++
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b84d2976e31d5cc3a9b6547d0c4b02a61327ce0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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