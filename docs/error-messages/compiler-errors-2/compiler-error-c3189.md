---
title: Błąd kompilatora C3189
ms.date: 11/04/2016
f1_keywords:
- C3189
helpviewer_keywords:
- C3189
ms.assetid: b254de79-931e-4a59-a9f4-1c690d90ca5e
ms.openlocfilehash: fe9dc38748fd667734c5d80f1284348184fed450
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456982"
---
# <a name="compiler-error-c3189"></a>Błąd kompilatora C3189

"typeid\<wpisz abstrakcyjnym deklaratorze >": Ta składnia nie jest już obsługiwana, należy użyć:: typeid zamiast tego

Przestarzałe formie [typeid](../../windows/typeid-cpp-component-extensions.md) był używany, za pomocą nowego formularza.

Poniższy przykład spowoduje wygenerowanie C3189:

```
// C3189.cpp
// compile with: /clr
int main() {
   System::Type^ t  = typeid<System::Object>;   // C3189
   System::Type^ t2  = System::Object::typeid;   // OK
}
```