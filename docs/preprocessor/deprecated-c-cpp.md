---
title: przestarzała wartość dyrektywy pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.deprecated
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
ms.openlocfilehash: 52d9deb4ad68dacc99fab9d12bc9eb21bc0d360e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231614"
---
# <a name="deprecated-pragma"></a>przestarzała wartość dyrektywy pragma

**`deprecated`** Pragma umożliwia wskazanie, że funkcja, typ lub inny identyfikator nie może być już obsługiwany w przyszłej wersji lub nie powinien już być używany.

> [!NOTE]
> Aby uzyskać informacje o atrybucie C++ 14 `[[deprecated]]` i wskazówki dotyczące sytuacji, w których należy używać tego atrybutu zamiast `__declspec(deprecated)` modyfikatora Microsoft lub **`deprecated`** pragma, zobacz [atrybuty w języku C++](../cpp/attributes.md).

## <a name="syntax"></a>Składnia

> **#pragma przestarzałe (** *Identifier1* [ **,** *identifier2* ...] **)**

## <a name="remarks"></a>Uwagi

Gdy kompilator napotka identyfikator określony przez **`deprecated`** pragma, wystawia ostrzeżenia kompilatora [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md).

Można przestarzałe nazwy makr. Umieść nazwę makra w cudzysłowie lub w przeciwnym razie nastąpi rozwinięcie makra.

Ze względu na to, że **`deprecated`** pragma działa na wszystkich zgodnych identyfikatorach i nie uwzględnia podpisów, nie jest najlepszą opcją dla przestarzałych określonych wersji funkcji przeciążonych. Wszystkie zgodne nazwy funkcji, które są wprowadzane do zakresu wyzwalają ostrzeżenie.

Zalecamy użycie atrybutu C++ 14 `[[deprecated]]` , jeśli jest to możliwe, zamiast **`deprecated`** dyrektywy pragma. Modyfikator deklaracji __declspec specyficzny dla firmy Microsoft [(przestarzały)](../cpp/deprecated-cpp.md) jest również lepszym wyborem w wielu przypadkach niż **`deprecated`** pragma. `[[deprecated]]`Atrybut i `__declspec(deprecated)` modyfikator umożliwiają określanie przestarzałego stanu dla konkretnych formularzy przeciążonych funkcji. Ostrzeżenie diagnostyczne pojawia się tylko w odniesieniu do określonej przeciążonej funkcji, której dotyczy atrybut lub modyfikator.

## <a name="example"></a>Przykład

```cpp
// pragma_directive_deprecated.cpp
// compile with: /W3
#include <stdio.h>
void func1(void) {
}

void func2(void) {
}

int main() {
   func1();
   func2();
   #pragma deprecated(func1, func2)
   func1();   // C4995
   func2();   // C4995
}
```

Poniższy przykład pokazuje, jak zastąpić klasę:

```cpp
// pragma_directive_deprecated2.cpp
// compile with: /W3
#pragma deprecated(X)
class X {  // C4995
public:
   void f(){}
};

int main() {
   X x;   // C4995
}
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
