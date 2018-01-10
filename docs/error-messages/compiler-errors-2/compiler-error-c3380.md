---
title: "C3380 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3380
dev_langs: C++
helpviewer_keywords: C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f8789889ab0d9ebe93941a438c286ed718ac4721
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3380"></a>C3380 błąd kompilatora
"class": Nieprawidłowy specyfikator dostępu do zestawu - tylko "public" lub "private" są dozwolone  
  
 Gdy jest stosowany do zarządzanej klasy lub struktury, [publicznego](../../cpp/public-cpp.md) i [prywatnej](../../cpp/private-cpp.md) słowa kluczowe wskazuje, czy mają być widoczne klasy przy użyciu metadanych zestawu. Tylko `public` lub `private` może odnosić się do klasy w programie skompilowane z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 `ref` i `value` słów kluczowych, gdy jest używany z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), wskazuje, że klasa jest zarządzane (zobacz [klas i struktur](../../windows/classes-and-structs-cpp-component-extensions.md)).  
  
 Poniższy przykład generuje C3380:  
  
```  
// C3380_2.cpp  
// compile with: /clr  
protected ref class A {   // C3380  
// try the following line instead  
// ref class A {  
public:  
   static int i = 9;  
};  
  
int main() {  
   A^ myA = gcnew A;  
   System::Console::WriteLine(myA->i);  
}  
```  
