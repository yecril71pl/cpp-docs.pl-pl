---
title: Błąd kompilatora C2228 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2228
dev_langs:
- C++
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70ea4fcdf2647264550b32ce941a3551664a6b94
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082883"
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