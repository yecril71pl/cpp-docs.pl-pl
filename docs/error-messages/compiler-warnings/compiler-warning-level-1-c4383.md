---
title: Kompilator ostrzeżenie (poziom 1) C4383
ms.date: 11/04/2016
f1_keywords:
- C4383
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
ms.openlocfilehash: 2510dda59047632e2a4823f734feeffd0c0a5b02
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58778042"
---
# <a name="compiler-warning-level-1-c4383"></a>Kompilator ostrzeżenie (poziom 1) C4383

"instance_dereference_operator": znaczenie usunięcia odwołania do dojścia mogą ulec zmianie, gdy istnieje operatorów zdefiniowanych przez użytkownika 'operator'; Zapisz operator jako funkcję statyczną aby była niejawna przy korzystaniu z operandu

Po dodaniu zastępowania wystąpienia zdefiniowanych przez użytkownika operator wyłuskania w typ zarządzany, potencjalnie zastąpienie operator wyłuskania typu możliwość zwracania uchwyt obiektu. Należy wziąć pod uwagę pisanie statycznych, zdefiniowane przez użytkownika operator dereferencji.

Aby uzyskać więcej informacji, zobacz [Operator uchwytu do obiektu (^)](../../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) i [Tracking Reference Operator](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

Ponadto operator wystąpienia nie jest dostępna dla innych kompilatorów języka za pomocą odwołania metadanych. Aby uzyskać więcej informacji, zobacz [operatory zdefiniowane przez użytkownika (C + +/ CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4383.

```
// C4383.cpp
// compile with: /clr /W1

ref struct S {
   int operator*() { return 0; }   // C4383
};

ref struct T {
   static int operator*(T%) { return 0; }
};

int main() {
   S s;
   S^ pS = %s;

   T t;
   T^ pT = %t;
   T% rT = *pT;
}
```