---
title: C3367 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3367
dev_langs:
- C++
helpviewer_keywords:
- C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2884e38d1ad1aecef8e7b0723674ebd9849d8f40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3367"></a>C3367 błąd kompilatora
"static_member_function": nie można użyć statycznej funkcji by utworzyć niezwiązanego delegata  
  
Podczas wywoływania niezwiązanego delegata musi przejść pomyślnie wystąpienia obiektu. Ponieważ funkcja statyczny element członkowski jest wywoływana za pomocą nazwy klasy, można tylko wystąpienia niezwiązanego delegata z funkcję elementu członkowskiego wystąpienia.  
  
Aby uzyskać więcej informacji na temat niezwiązane obiekty delegowane, zobacz [porady: definiowanie i użycie deleguje (C + +/ CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md).  
  
## <a name="example"></a>Przykład  
Poniższy przykład generuje C3367.  
  
```cpp  
// C3367.cpp  
// compile with: /clr  
ref struct R {  
   void b() {}  
   static void f() {}  
};  
  
delegate void Del(R^);  
  
int main() {  
   Del ^ a = gcnew Del(&R::b);   // OK  
   Del ^ b = gcnew Del(&R::f);   // C3367  
}  
```