---
title: "C3821 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3821
dev_langs:
- C++
helpviewer_keywords:
- C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eda98ddd6247a2b3d137c015e5e4e3b06f04d821
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3821"></a>C3821 błąd kompilatora
"Funkcja": typ zarządzany lub funkcja nie można użyć w funkcji niezarządzanej  
  
 Funkcji w zestawie wbudowanym lub [setjmp](../../c-runtime-library/reference/setjmp.md) nie może zawierać typy wartości lub klasy zarządzane. Aby naprawić ten błąd, należy usunąć wbudowany zestaw i `setjmp` lub usunięcie zarządzanych obiektów.  
  
 C3821 może również wystąpić, Jeśli spróbujesz użyć automatycznego magazynu w funkcji vararg.  Aby uzyskać więcej informacji, zobacz [zmiennej listy argumentów (...) (C + +/ CLI) ](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md) i [semantyka stosu C++ dla typów referencyjnych](../../dotnet/cpp-stack-semantics-for-reference-types.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3821.  
  
```  
// C3821a.cpp  
// compile with: /clr /c  
public ref struct R {};  
void test1(...) {  
   R r;   // C3821  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3821.  
  
```  
// C3821b.cpp  
// compile with: /clr  
// processor: /x86  
ref class A {  
   public:  
   int i;  
};  
  
int main() {  
   // cannot use managed classes in this function  
   A ^a;     
  
   __asm {  
      nop  
   }  
} // C3821  
```  
