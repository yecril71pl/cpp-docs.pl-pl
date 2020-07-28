---
title: Ostrzeżenie kompilatora (poziom 3) C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: f9d3875fdc17def1e7d3bcb72149c5faf90f656a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220057"
---
# <a name="compiler-warning-level-3-c4101"></a>Ostrzeżenie kompilatora (poziom 3) C4101

"Identyfikator": niereferencyjna zmienna lokalna

Zmienna lokalna nie jest nigdy używana. To ostrzeżenie będzie miało miejsce w oczywistej sytuacji:

```cpp
// C4101a.cpp
// compile with: /W3
int main() {
int i;   // C4101
}
```

Jednak to ostrzeżenie również występuje podczas wywoływania **`static`** funkcji składowej za pomocą wystąpienia klasy:

```cpp
// C4101b.cpp
// compile with:  /W3
struct S {
   static int func()
   {
      return 1;
   }
};

int main() {
   S si;   // C4101, si is never used
   int y = si.func();
   return y;
}
```

W tej sytuacji kompilator używa informacji o `si` dostępie do **`static`** funkcji, ale wystąpienie klasy nie jest konieczne do wywołania **`static`** funkcji; w związku z tym ostrzeżenie. Aby rozwiązać ten problem, możesz:

- Dodaj Konstruktor, w którym kompilator będzie używać wystąpienia elementu `si` w wywołaniu `func` .

- Usuń **`static`** słowo kluczowe z definicji `func` .

- Wywołaj **`static`** funkcję jawnie: `int y = S::func();` .
