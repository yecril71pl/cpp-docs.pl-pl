---
title: Błąd kompilatora C2438 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2438
dev_langs:
- C++
helpviewer_keywords:
- C2438
ms.assetid: 3a0ab3ba-d0e4-4d8f-971d-e503397cc827
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f5153e3ff6626f3ea1b1155f14bc9ef96441e7d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066079"
---
# <a name="compiler-error-c2438"></a>Błąd kompilatora C2438

'Identyfikator': nie można zainicjować danych statycznej klasy poprzez Konstruktor

Konstruktor jest używany do inicjowania statycznej składowej klasy. Statyczne elementy członkowskie muszą być zainicjowane w definicji poza deklaracją klasy.

Poniższy przykład spowoduje wygenerowanie C2438:

```
// C2438.cpp
struct X {
   X(int i) : j(i) {}   // C2438
   static int j;
};

int X::j;

int main() {
   X::j = 1;
}
```