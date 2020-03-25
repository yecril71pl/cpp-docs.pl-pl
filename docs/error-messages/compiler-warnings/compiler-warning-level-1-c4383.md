---
title: Ostrzeżenie kompilatora (poziom 1) C4383
ms.date: 11/04/2016
f1_keywords:
- C4383
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
ms.openlocfilehash: 1c4a7ca806430c73c8e8396e596782253cc06f09
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162741"
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
