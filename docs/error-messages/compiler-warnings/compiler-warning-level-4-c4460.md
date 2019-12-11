---
title: Ostrzeżenie kompilatora (poziom 4) C4460
ms.date: 11/04/2016
f1_keywords:
- C4460
helpviewer_keywords:
- C4460
ms.assetid: c97ac1c9-598d-479e-bfff-c993690c4f3d
ms.openlocfilehash: 1b4ec02211dc346c1672b403bf8af16dc6fca461
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990799"
---
# <a name="compiler-warning-level-4-c4460"></a>Ostrzeżenie kompilatora (poziom 4) C4460

Operator WinRT lub CLR "operator" ma parametr zakończony przez odwołanie. Operator WinRT lub CLR ma inną semantykę z C++ operatora "operator", czy chodziło o wartość?

Wartość została przeniesiona przez odwołanie do zdefiniowanej przez użytkownika środowisko wykonawcze systemu Windows lub operatora CLR. Jeśli wartość zostanie zmieniona wewnątrz funkcji, należy pamiętać, że wartość zwracana po wywołaniu funkcji zostanie przypisana wartość zwracana funkcji. W warstwie C++standardowa zmieniona wartość jest odzwierciedlona po wywołaniu funkcji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4460 i pokazuje, jak rozwiązać ten problem.

```cpp
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
