---
title: Brakująca treść funkcji lub zmienna
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 6d2ef22b90009d320485fb6fe3f7e308ae05c442
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173624"
---
# <a name="missing-function-body-or-variable"></a>Brakująca treść funkcji lub zmienna

Za pomocą tylko prototypu funkcji kompilator może kontynuować bez błędu, ale konsolidator nie może rozpoznać wywołania do adresu, ponieważ nie istnieje kod funkcji ani zarezerwowane miejsce na zmienne. Ten błąd nie zostanie wyświetlony do momentu utworzenia wywołania funkcji, którą konsolidator musi rozpoznać.

## <a name="example"></a>Przykład

Wywołanie funkcji w głównym spowoduje wystąpienie LNK2019, ponieważ prototyp umożliwia kompilatorowi określenie, że funkcja już istnieje.  Konsolidator stwierdzi, że nie.

```cpp
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>Przykład

W C++programie upewnij się, że dołączysz implementację określonej funkcji dla klasy, a nie tylko prototyp w definicji klasy. Jeśli definiujesz klasę poza plikiem nagłówkowym, pamiętaj o uwzględnieniu nazwy klasy przed funkcją (`Classname::memberfunction`).

```cpp
// LNK2019_MFBV_2.cpp
// LNK2019 expected
struct A {
   static void Test();
};

// Should be void A::Test() {}
void Test() {}

int main() {
   A AObject;
   AObject.Test();
}
```

## <a name="see-also"></a>Zobacz też

[Błąd narzędzi konsolidatora LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
