---
title: "C3104 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3104
dev_langs: C++
helpviewer_keywords: C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 837ff564bc3b2795bce6de69caa85e1d1dcf2766
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3104"></a>C3104 błąd kompilatora
argument atrybutu niedozwolony  
  
 Określono nieprawidłowy argument atrybutu.  
  
 Zobacz [typy parametrów atrybutu](../../windows/attribute-parameter-types-cpp-component-extensions.md) Aby uzyskać więcej informacji.  
  
 Ten błąd może być wygenerowanego w wyniku pracy zgodność kompilatora, która została wykonana dla Visual C++ 2005: podczas przekazywania tablic do atrybutów niestandardowych, typu tablicy określa się już na liście inicjalizacji agregacji. Kompilator teraz wymaga określenia typu tablicy, jak również na liście inicjatora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3104.  
  
```  
// C3104a.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::Class)]  
public ref struct ABC : public Attribute {  
   ABC(array<int>^){}  
   array<double> ^ param;  
};  
  
[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104  
// try the following line instead  
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]   
ref struct AStruct{};  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3104.  
  
```  
// C3104b.cpp  
// compile with: /clr /c  
// C3104 expected  
using namespace System;  
  
int func() {  
   return 0;   
}  
  
[attribute(All)]  
ref class A {  
public:   
   A(int) {}  
};  
  
// Delete the following 2 lines to resolve.  
[A(func())]  
ref class B {};  
  
// OK  
[A(0)]  
ref class B {};  
```  
