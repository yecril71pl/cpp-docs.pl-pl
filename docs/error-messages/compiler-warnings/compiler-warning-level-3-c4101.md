---
title: Kompilator ostrzeżenie (poziom 3) C4101 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4101
dev_langs:
- C++
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1549a327329d438cb30bd6908e07419eb1b6bc1a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060840"
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