---
title: C2217 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2217
dev_langs:
- C++
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7c60ac95be1a0b21ed2cb7df43117ff7ece7a39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172267"
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