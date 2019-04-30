---
title: Kompilator ostrzeżenie (poziom 3) C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: d1109a32e754a6055e5e1d90632ad85332d832f1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402323"
---
# <a name="compiler-warning-level-3-c4101"></a>Kompilator ostrzeżenie (poziom 3) C4101

'Identyfikator': nieużywanej zmienna lokalna

Zmienna lokalna nigdy nie jest używany. To ostrzeżenie wystąpi w oczywisty sytuacji:

```
// C4101a.cpp
// compile with: /W3
int main() {
int i;   // C4101
}
```

Jednak to ostrzeżenie wystąpi również podczas wywoływania **statyczne** funkcja elementu członkowskiego przez wystąpienie klasy:

```
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

W takiej sytuacji, kompilator używa informacji o `si` dostęp do **statyczne** funkcji, ale wystąpienia klasy nie jest potrzebna do wywołania **statyczne** funkcji; dlatego ostrzeżenia. Aby rozwiązać tego ostrzeżenia, można wykonać następujące akcje:

- Dodaj Konstruktor, w którym kompilator użyje wystąpienia `si` w wywołaniu `func`.

- Usuń **statyczne** — słowo kluczowe w definicji `func`.

- Wywołaj **statyczne** funkcji jawnie: `int y = S::func();`.