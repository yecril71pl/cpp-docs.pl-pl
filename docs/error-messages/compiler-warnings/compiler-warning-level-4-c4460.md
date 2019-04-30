---
title: Kompilator ostrzeżenie (poziom 4) C4460
ms.date: 11/04/2016
f1_keywords:
- C4460
helpviewer_keywords:
- C4460
ms.assetid: c97ac1c9-598d-479e-bfff-c993690c4f3d
ms.openlocfilehash: a42562a2c35bb56de4ce7147e199f4db2dddb684
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400815"
---
# <a name="compiler-warning-level-4-c4460"></a>Kompilator ostrzeżenie (poziom 4) C4460

WinRT, czy CLR operator 'operator', ma parametr przekazywany przez odwołanie. WinRT, czy CLR operator 'operator' ma semantykę różną od operatora C++ "operator", czy zamierzasz przekazać przez wartość?

Wartość jest przekazywany przez odwołanie do operatorów środowiska wykonawczego Windows, czy CLR zdefiniowane przez użytkownika. Jeśli wartość zostanie zmieniona w funkcję, należy pamiętać, że wartość zwracana po wywołaniu funkcji zostanie przypisana wartość zwracaną przez funkcję. W standardzie języka C++ zmieniona wartość jest widoczna po wywołaniu funkcji.

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