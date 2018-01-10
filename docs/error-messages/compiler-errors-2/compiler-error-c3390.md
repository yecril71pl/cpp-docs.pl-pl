---
title: "C3390 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3390
dev_langs: C++
helpviewer_keywords: C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ea23a13a338e5d09eac0714914d9c1020b5908cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3390"></a>C3390 błąd kompilatora
"type_arg": nieprawidłowy typ argumentu dla parametru ogólnego "param" Ogólne "generic_type" musi być typem referencyjnym  
  
Niepoprawnie wystąpienia typu ogólnego.  Sprawdź definicję typu.  Aby uzyskać więcej informacji, zobacz [ogólne](../../windows/generics-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
Używa pierwszej próbie C# do tworzenia składnika, który zawiera typu ogólnego, który ma pewne ograniczenia, które nie są obsługiwane podczas tworzenia typów ogólnych w języku C + +/ CLR. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).  
  
```cs  
// C3390.cs  
// Compile by using: csc /target:library C3390.cs  
// a C# program  
public class GR<C, V, N>  
where C : class  
where V : struct  
where N : new() {}  
```  
  
Poniższy przykładowy składnik C3390.dll jest dostępny, generuje C3390.  
  
```cpp  
// C3390_b.cpp  
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>  
ref class R { R(int) {} };  
value class V {};  
ref struct N { N() {} };  
  
int main () {  
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type  
   GR<R^, V, N^>^ gr2b; // OK  
}  
```