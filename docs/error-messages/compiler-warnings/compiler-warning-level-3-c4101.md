---
title: Ostrzeżenie kompilatora (poziom 3) C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: 0ac34fbaf4cbb54583394dff5b8645fe56b8b9cd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199048"
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

Jednak to ostrzeżenie również występuje podczas wywoływania **statycznej** funkcji składowej za pomocą wystąpienia klasy:

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

W tej sytuacji kompilator używa informacji o `si`, aby uzyskać dostęp do funkcji **statycznej** , ale wystąpienie klasy nie jest konieczne do wywołania funkcji **statycznej** ; w związku z tym ostrzeżeniem. Aby rozwiązać ten problem, możesz:

- Dodaj Konstruktor, w którym kompilator będzie używać wystąpienia `si` w wywołaniu `func`.

- Usuń słowo kluczowe **static** z definicji `func`.

- Jawnie wywołaj funkcję **statyczną** : `int y = S::func();`.
