---
title: przestarzała wartość dyrektywy pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.deprecated
- deprecated_CPP
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
ms.openlocfilehash: 2e76d1c53cb900c108e2839a9aad17b330143a5d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222404"
---
# <a name="deprecated-pragma"></a>przestarzała wartość dyrektywy pragma

**Zaniechana** pragma umożliwia wskazanie, że funkcja, typ lub inny identyfikator nie może być już obsługiwany w przyszłej wersji lub nie powinien już być używany.

> [!NOTE]
> Aby uzyskać informacje o atrybucie c++ `[[deprecated]]` 14 i wskazówki dotyczące sytuacji, w których należy używać tego atrybutu zamiast modyfikatora Microsoft `__declspec(deprecated)` lub **przestarzałej** dyrektywy pragma, zobacz [atrybuty w C++ ](../cpp/attributes.md).

## <a name="syntax"></a>Składnia

> **#pragma przestarzałe (** *Identifier1* [ **,** *identifier2* ...] **)**

## <a name="remarks"></a>Uwagi

Gdy kompilator napotka identyfikator określony przez przestarzałą pragmę , wystawia ostrzeżenia kompilatora [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md).

Można przestarzałe nazwy makr. Umieść nazwę makra w cudzysłowie lub w przeciwnym razie nastąpi rozwinięcie makra.

Ponieważ **zaniechana** pragma działa na wszystkich zgodnych identyfikatorach i nie uwzględnia podpisów, nie jest najlepszą opcją dla przestarzałych określonych wersji funkcji przeciążonych. Wszystkie zgodne nazwy funkcji, które są wprowadzane do zakresu wyzwalają ostrzeżenie.

Zalecamy użycie atrybutu c++ 14 `[[deprecated]]` , jeśli jest to możliwe, zamiast **przestarzałej** dyrektywy pragma. Modyfikator deklaracji [__declspec (przestarzały)](../cpp/deprecated-cpp.md) firmy Microsoft jest również lepszym wyborem w wielu przypadkach niż w przypadku **przestarzałej** dyrektywy pragma. `[[deprecated]]` Atrybut i`__declspec(deprecated)` modyfikator umożliwiają określanie przestarzałego stanu dla konkretnych formularzy przeciążonych funkcji. Ostrzeżenie diagnostyczne pojawia się tylko w odniesieniu do określonej przeciążonej funkcji, której dotyczy atrybut lub modyfikator.

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