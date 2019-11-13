---
title: Ostrzeżenie kompilatora (poziom 1) C4383
ms.date: 11/04/2016
f1_keywords:
- C4383
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
ms.openlocfilehash: 9681408841173bad4aca3305e727ddde6cd98f14
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966171"
---
# <a name="compiler-warning-level-1-c4383"></a>Ostrzeżenie kompilatora (poziom 1) C4383

"instance_dereference_operator": znaczenie usunięcia odwołania do uchwytu może się zmienić, gdy istnieje operator "operator" zdefiniowany przez użytkownika; Napisz operator jako funkcję statyczną, aby być jawnym o operandzie

Po dodaniu przesłonięcia wystąpienia zdefiniowanego przez użytkownika do operatora dereferencji w typie zarządzanym można zastąpić operator dereferencji typu, aby zwracał obiekt dojścia. Rozważ zapisanie statycznego, zdefiniowanego przez użytkownika operatora dereferencji.

Aby uzyskać więcej informacji, zobacz [uchwyt do operatora obiektu (^)](../../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) i [operator odwołania śledzącego](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

Ponadto operator wystąpienia nie jest dostępny dla innych kompilatorów języka za pośrednictwem metadanych, których dotyczy odwołanie. Aby uzyskać więcej informacji, zobacz [Operatory zdefiniowane przez użytkownikaC++(/CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4383.

```cpp
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