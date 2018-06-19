---
title: C3380 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3380
dev_langs:
- C++
helpviewer_keywords:
- C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 315031946f9a89f53097e4c2371286fba213f698
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252451"
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
