---
title: Błąd kompilatora C2228
ms.date: 11/04/2016
f1_keywords:
- C2228
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
ms.openlocfilehash: 20e295d09e39a12ed8163ec980fa304cd4167218
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628400"
---
# <a name="compiler-error-c2228"></a>Błąd kompilatora C2228

po lewej stronie ".identifier" musi mieć klasy/struct/union

Argument po lewej stronie kropki (.) nie jest klasy, struktury lub Unii.

Poniższy przykład spowoduje wygenerowanie C2228:

```
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

Również zostanie wyświetlony ten błąd, jeśli używasz Błędna składnia w przypadku korzystania z zarządzanych rozszerzeń. Operator kropki innych języków Visual Studio umożliwia uzyskiwanie dostępu do członka klasy zarządzanej, wskaźnik do obiektu w języku C++ oznacza, trzeba użyć -> — operator do dostępu do elementu członkowskiego:

Problem: `String * myString = checkedListBox1->CheckedItems->Item[0].ToString();`

Po prawej stronie: `String * myString = checkedListBox1->CheckedItems->Item[0]->ToString();`