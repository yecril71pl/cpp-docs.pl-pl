---
title: "C2217 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2217
dev_langs: C++
helpviewer_keywords: C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0f1795534af1332859fd1a33a137573df82643b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2217"></a>C2217 błąd kompilatora
"attribute1" wymaga "attribute2"  
  
 Pierwszy atrybut funkcja wymaga drugiego atrybutu.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Przerwań (`__interrupt`) funkcja zadeklarowana jako `near`. Przerwania funkcji musi być `far`.  
  
2.  Funkcja zadeklarowana ze przerwań `__stdcall`, lub `__fastcall`. Funkcje przerwania muszą Użyj C konwencji wywoływania.  
  
## <a name="example"></a>Przykład  
 C2217 może również wystąpić, jeśli chcesz powiązać delegata funkcji CLR, która przyjmuje zmienną liczbę argumentów. Jeśli funkcja ma również e param tablicy przeciążenia, użyj zamiast tego. Poniższy przykład generuje C2217.  
  
```  
// C2217.cpp  
// compile with: /clr  
using namespace System;  
delegate void MyDel(String^, Object^, Object^, ...);   // C2217  
delegate void MyDel2(String ^, array<Object ^> ^);   // OK  
  
int main() {  
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);  
   array<Object ^ > ^ x = gcnew array<Object ^>(2);  
   x[0] = safe_cast<Object^>(0);  
   x[1] = safe_cast<Object^>(1);  
  
   // wl("{0}, {1}", 0, 1);  
   wl("{0}, {1}", x);  
}  
```