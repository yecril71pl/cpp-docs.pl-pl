---
title: Błąd kompilatora C2228
ms.date: 11/04/2016
f1_keywords:
- C2228
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
ms.openlocfilehash: 56eed6aeff5a955253a440d5931d66118f4604e0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759285"
---
# <a name="compiler-error-c2228"></a>Błąd kompilatora C2228

po lewej ". identyfikator" musi być klasą/strukturą/Unią

Operand z lewej strony kropki (.) nie jest klasą, strukturą ani Unią.

Poniższy przykład generuje C2228:

```cpp
// C2228.cpp
int i;
struct S {
public:
    int member;
} s, *ps = &s;

int main() {
   i.member = 0;   // C2228 i is not a class type
   ps.member = 0;  // C2228 ps is a pointer to a structure

   s.member = 0;   // s is a structure type
   ps->member = 0; // ps points to a structure S
}
```

Ten błąd zostanie również wyświetlony, jeśli podczas korzystania z rozszerzeń zarządzanych użyto nieprawidłowej składni. W innych językach programu Visual Studio można użyć operatora kropki w celu uzyskania dostępu do elementu członkowskiego klasy zarządzanej, wskaźnika do obiektu w programie C++ , aby uzyskać dostęp do elementu członkowskiego przy użyciu operatora->:

Nieprawidłowy: `String * myString = checkedListBox1->CheckedItems->Item[0].ToString();`

Prawo: `String * myString = checkedListBox1->CheckedItems->Item[0]->ToString();`
