---
title: Kompilatora (poziom 4) ostrzeżenie C4487 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4487
dev_langs:
- C++
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80008dbcfbebe4e91398e651e361efe7df30b641
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293185"
---
# <a name="compiler-warning-level-4-c4487"></a>Kompilator C4487 ostrzegawcze (poziom 4)
"derived_class_function": pasuje do dziedziczonej metody niewirtualnej "base_class_function", ale nie jest jawnie oznaczony jako "new"  
  
 Funkcja w klasie pochodnej ma taką samą sygnaturę jak funkcja-wirtualnej klasy podstawowej. C4487 przypomina o tym, że funkcja klasy pochodnej nie przesłania funkcji klasy podstawowej. Znak jawnie funkcji klasy pochodnej jako `new` rozwiązywać to ostrzeżenie.  
  
 Aby uzyskać więcej informacji, zobacz [new (nowe gniazdo w vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4487.  
  
```  
// C4487.cpp  
// compile with: /W4 /clr  
using namespace System;  
public ref struct B {  
   void f() { Console::WriteLine("in B::f"); }  
   void g() { Console::WriteLine("in B::g"); }  
};  
  
public ref struct D : B {  
   void f() { Console::WriteLine("in D::f"); }   // C4487  
   void g() new { Console::WriteLine("in D::g"); }   // OK  
};  
  
int main() {  
   B ^ a = gcnew D;  
   // will call base class functions  
   a->f();  
   a->g();  
}  
```