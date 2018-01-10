---
title: "C3225 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3225
dev_langs: C++
helpviewer_keywords: C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9c189e2f4a0af7363f5bb988c9911bd90eb72809
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3225"></a>C3225 błąd kompilatora
argument typu generycznego dla "arg" nie może być "type", musi być typem wartości lub typ dojścia  
  
 Argument typu generycznego nie ma poprawnego typu.  
  
 Aby uzyskać więcej informacji, zobacz [ogólne](../../windows/generics-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
 Nie można utworzyć wystąpienia typu ogólnego typu macierzystego. Poniższy przykład generuje C3225.  
  
```  
// C3225.cpp  
// compile with: /clr  
class A {};  
  
ref class B {};  
  
generic <class T>  
ref class C {};  
  
int main() {  
   C<A>^ c = gcnew C<A>;   // C3225  
   C<B^>^ c2 = gcnew C<B^>;   // OK  
}  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie tworzone składnika za pomocą języka C#. Należy zauważyć, że ograniczenie Określa, że typ ogólny można wdrożyć tylko z typem wartości.  
  
```  
// C3225_b.cs  
// compile with: /target:library  
// a C# program  
public class MyList<T> where T: struct {}  
```  
  
## <a name="example"></a>Przykład  
 Ten przykład wykorzystuje C# — utworzone składnika i narusza ograniczenie, które mogą być tylko MyList utworzyć wystąpienia typu wartości innych niż <xref:System.Nullable>. Poniższy przykład generuje C3225.  
  
```  
// C3225_c.cpp  
// compile with: /clr  
#using "C3225_b.dll"  
ref class A {};  
value class B {};  
int main() {  
   MyList<A> x;   // C3225  
   MyList<B> y;   // OK  
}  
```