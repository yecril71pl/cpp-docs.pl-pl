---
title: "C3379 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3379
dev_langs: C++
helpviewer_keywords: C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e6fa111a525d81c418d3285c05af86b700e8cb08
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3379"></a>C3379 błąd kompilatora
"class": zagnieżdżona klasa nie może mieć specyfikatora dostępu do zestawu jako części swojej deklaracji  
  
 Gdy jest stosowany do typu zarządzanego, takich jak klasy lub struktury, [publicznego](../../cpp/public-cpp.md) i [prywatnej](../../cpp/private-cpp.md) słowa kluczowe wskazuje, czy mają być widoczne klasy przy użyciu metadanych zestawu. `public`lub `private` nie można zastosować do zagnieżdżona klasa będzie dziedziczyć dostęp do zestawu klasy otaczającej.  
  
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
