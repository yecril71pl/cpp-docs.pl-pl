---
title: "Kompilatora (poziom 4) ostrzeżenie C4460 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4460
dev_langs: C++
helpviewer_keywords: C4460
ms.assetid: c97ac1c9-598d-479e-bfff-c993690c4f3d
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa925e8d0ef7779f21485cb154b9b9209ce2388e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4460"></a>Kompilator C4460 ostrzegawcze (poziom 4)
WinRT lub CLR operatora "operator", ma parametr przekazywany przez odwołanie. WinRT lub CLR operatora "operator" ma semantykę różną od operatora C++ "operator", czy zamierzasz przekazanie przez wartość?  
  
 Wartość jest przekazywana przez odwołanie do operator środowiska wykonawczego systemu Windows lub CLR zdefiniowane przez użytkownika. Jeśli wartość została zmieniona wewnątrz funkcji, należy pamiętać, zwracana wartość po wywołaniu funkcji zostanie przypisana wartość zwracana funkcji. W języku C++ standardowe zmieniona wartość jest widoczny po wywołaniu funkcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4460 i pokazuje, jak go naprawić.  
  
```  
// C4460.cpp  
// compile with: /W4 /clr   
#include <stdio.h>  
  
public value struct V {  
   static V operator ++(V& me) {   // C4460  
   // try the following line instead  
   // static V operator ++(V me) {  
  
      printf_s(__FUNCSIG__ " called\n");  
      V tmp = me;  
      me.m_i++;  
      return tmp;  
   }  
   int m_i;  
};  
  
int main() {  
   V v;  
   v.m_i = 0;  
  
   printf_s("%d\n", v.m_i);   // Should print 0  
   v++;   // Translates to "v = V::operator ++(v)"  
   printf_s("%d\n", v.m_i);   // will print 0, hence the warning  
}  
```