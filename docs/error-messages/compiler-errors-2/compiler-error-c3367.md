---
title: "C3367 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3367
dev_langs: C++
helpviewer_keywords: C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d1d144399ca42ba321d8f3d11425bf2ff8e65891
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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