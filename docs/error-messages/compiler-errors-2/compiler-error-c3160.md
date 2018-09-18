---
title: Błąd kompilatora C3160 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3160
dev_langs:
- C++
helpviewer_keywords:
- C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf3ecc18e1afc9b13e47ad8b20bb92f7686d0cfc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042276"
---
# <a name="compiler-error-c3160"></a>Błąd kompilatora C3160

"wskaźnik": element członkowski danych zarządzanej lub klasa WinRT nie może mieć tego typu

Wskaźniki kolekcji wyrzucania elementów wewnętrznych mogą wskazywać na wnętrze zarządzanej lub klasa WinRT. Ponieważ są wolniejsze od wskaźniki całego obiektu i wymagają specjalnej obsługi przez moduł odśmiecania pamięci, nie można zadeklarować wewnętrznymi wskaźnikami zarządzanymi jako elementy członkowskie klasy.

Poniższy przykład spowoduje wygenerowanie C3160:

```
// C3160.cpp
// compile with: /clr
ref struct A {
   // cannot create interior pointers inside a class
   interior_ptr<int> pg;   // C3160
   int g;   // OK
   int* pg2;   // OK
};

int main() {
   interior_ptr<int> pg2;   // OK
}
```
