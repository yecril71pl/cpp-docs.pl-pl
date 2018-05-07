---
title: Kompilatora (poziom 1) ostrzeżenie C4383 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4383
dev_langs:
- C++
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b78209cf4e3e320cca8b161a4e6c99eaca6d771c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4383"></a>Kompilator C4383 ostrzegawcze (poziom 1)
"instance_dereference_operator": znaczenie usunięcia odwołania do dojścia można zmienić, gdy istnieje operatora zdefiniowanej przez użytkownika "operator'; Zapisz operator jako funkcję statyczną aby była niejawna przy korzystaniu z operandu  
  
 Po dodaniu zastąpienie wystąpienia zdefiniowane przez użytkownika operatora dereference w typu zarządzanego potencjalnie zastąpić możliwość zwracania uchwytu obiektu typu dereference operatora. Należy wziąć pod uwagę zapisywania static, zdefiniowana przez użytkownika operatora anulowania odwołania do.  
  
 Aby uzyskać więcej informacji, zobacz [Operator uchwytu do obiektu (^)](../../windows/handle-to-object-operator-hat-cpp-component-extensions.md) i [Operator odwołania śledzenia](../../windows/tracking-reference-operator-cpp-component-extensions.md).  
  
 Ponadto operator wystąpienia nie jest dostępne inne Kompilatory języka przy użyciu metadanych do którego istnieje odwołanie. Aby uzyskać więcej informacji, zobacz [operatory zdefiniowane przez użytkownika (C + +/ CLI)](../../dotnet/user-defined-operators-cpp-cli.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4383.  
  
```  
// C4383.cpp  
// compile with: /clr /W1  
  
ref struct S {  
   int operator*() { return 0; }   // C4383  
};  
  
ref struct T {  
   static int operator*(T%) { return 0; }  
};   
  
int main() {  
   S s;  
   S^ pS = %s;  
  
   T t;  
   T^ pT = %t;  
   T% rT = *pT;  
}  
```