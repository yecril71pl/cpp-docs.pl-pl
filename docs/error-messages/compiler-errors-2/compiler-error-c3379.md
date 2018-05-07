---
title: C3379 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3379
dev_langs:
- C++
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ded7ebfba6ab9f9120ebfa48c1942209a74e704
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3379"></a>C3379 błąd kompilatora
"class": zagnieżdżona klasa nie może mieć specyfikatora dostępu do zestawu jako części swojej deklaracji  
  
 Gdy jest stosowany do typu zarządzanego, takich jak klasy lub struktury, [publicznego](../../cpp/public-cpp.md) i [prywatnej](../../cpp/private-cpp.md) słowa kluczowe wskazuje, czy mają być widoczne klasy przy użyciu metadanych zestawu. `public` lub `private` nie można zastosować do zagnieżdżona klasa będzie dziedziczyć dostęp do zestawu klasy otaczającej.  
  
 W przypadku użycia z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), `ref` i `value` słowa kluczowe wskazują, że klasa jest zarządzane (zobacz [klas i struktur](../../windows/classes-and-structs-cpp-component-extensions.md)).  
  
 Poniższy przykład generuje C3379:  
  
```  
// C3379a.cpp  
// compile with: /clr  
using namespace System;  
  
public ref class A {  
public:  
   static int i = 9;  
  
   public ref class BA {   // C3379  
   // try the following line instead  
   // ref class BA {  
   public:  
      static int ii = 8;  
   };  
};  
  
int main() {  
  
   A^ myA = gcnew A;  
   Console::WriteLine(myA->i);  
  
   A::BA^ myBA = gcnew A::BA;  
   Console::WriteLine(myBA->ii);  
}  
```  
