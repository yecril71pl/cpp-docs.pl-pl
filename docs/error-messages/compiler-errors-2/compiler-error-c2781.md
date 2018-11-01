---
title: Błąd kompilatora C2781
ms.date: 11/04/2016
f1_keywords:
- C2781
helpviewer_keywords:
- C2781
ms.assetid: f29b9963-f55b-427c-8db6-50f37713df5a
ms.openlocfilehash: be665d86cf230c364f522fd1ad74cd5a124ac9de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558967"
---
# <a name="compiler-error-c2781"></a>Błąd kompilatora C2781

"deklaracją": oczekuje co najmniej argument wartość1 - wartość2 podane

Za pomocą zmiennej listy parametrów szablonu funkcji ma za mało argumentów.

Poniższy przykład spowoduje wygenerowanie C2781:

```
// C2781.cpp
template<typename T>
void f(T, T, ...){}

int main() {
   f(1);   // C2781

   // try the following line instead
   f(1,1);
}
```