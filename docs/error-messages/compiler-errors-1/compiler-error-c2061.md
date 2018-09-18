---
title: Błąd kompilatora C2061 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2061
dev_langs:
- C++
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 896fdb21c57e0f558b87ec23e2be309cf49f8095
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057967"
---
# <a name="compiler-error-c2061"></a>Błąd kompilatora C2061

Błąd składniowy: identyfikator 'Identyfikator'

Kompilator znaleźć identyfikator, gdy nie był oczekiwany. Upewnij się, że `identifier` jest zadeklarowana, zanim go użyjesz.

Inicjator mogą być ujęte w nawiasy. Aby uniknąć tego problemu, należy umieścić specyfikator w nawiasach lub Przekształć go w `typedef`.

Również być przyczyną tego błędu, gdy kompilator wykryje wyrażenie jako argument szablonu klasy; Użyj [typename](../../cpp/typename.md) aby poinformować kompilator jest typem.

Poniższy przykład spowoduje wygenerowanie C2061:

```
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

C2061 może wystąpić w przypadku przekazania nazwy wystąpienia [typeid](../../windows/typeid-cpp-component-extensions.md):

```
// C2061b.cpp
// compile with: /clr
ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   System::Type ^ pType = typeid<pG>;   // C2061
   System::Type ^ pType2 = typeid<G>;   // OK
}
```