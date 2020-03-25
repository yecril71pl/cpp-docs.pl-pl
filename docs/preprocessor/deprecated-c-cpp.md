---
title: przestarzała wartość dyrektywy pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.deprecated
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
ms.openlocfilehash: 6caf5283aea848186c8bd6f9dd2009bb8d8ee8b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167631"
---
# <a name="deprecated-pragma"></a>przestarzała wartość dyrektywy pragma

**Zaniechana** pragma umożliwia wskazanie, że funkcja, typ lub inny identyfikator nie może być już obsługiwany w przyszłej wersji lub nie powinien już być używany.

> [!NOTE]
> Aby uzyskać informacje o atrybucie `[[deprecated]]` języka C++ 14 i wskazówki dotyczące sytuacji, w których należy używać tego atrybutu zamiast modyfikatora `__declspec(deprecated)` firmy Microsoft lub **przestarzałej** dyrektywy pragma, zobacz [atrybuty w C++ ](../cpp/attributes.md).

## <a name="syntax"></a>Składnia

> **#pragma przestarzałe (** *Identifier1* [ **,** *identifier2* ...] **)**

## <a name="remarks"></a>Uwagi

Gdy kompilator napotka identyfikator określony przez **przestarzałą** pragmę, wystawia ostrzeżenia kompilatora [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md).

Można przestarzałe nazwy makr. Umieść nazwę makra w cudzysłowie lub w przeciwnym razie nastąpi rozwinięcie makra.

Ponieważ **zaniechana** pragma działa na wszystkich zgodnych identyfikatorach i nie uwzględnia podpisów, nie jest najlepszą opcją dla przestarzałych określonych wersji funkcji przeciążonych. Wszystkie zgodne nazwy funkcji, które są wprowadzane do zakresu wyzwalają ostrzeżenie.

Zalecamy użycie atrybutu `[[deprecated]]` C++ 14, jeśli jest to możliwe, zamiast **przestarzałej** dyrektywy pragma. Modyfikator deklaracji __declspec specyficzny dla firmy Microsoft [(przestarzały)](../cpp/deprecated-cpp.md) jest również lepszym wyborem w wielu przypadkach niż **zaniechana** pragma. Atrybut `[[deprecated]]` i modyfikator `__declspec(deprecated)` umożliwiają określenie przestarzałego stanu dla określonych form przeciążonych funkcji. Ostrzeżenie diagnostyczne pojawia się tylko w odniesieniu do określonej przeciążonej funkcji, której dotyczy atrybut lub modyfikator.

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

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
