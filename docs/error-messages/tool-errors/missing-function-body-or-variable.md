---
title: Brakująca treść funkcji lub zmienna
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 5e3436054d69da7fb67c240c1d684585734635c3
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857155"
---
# <a name="missing-function-body-or-variable"></a>Brakująca treść funkcji lub zmienna

Po prostu prototypu funkcji kompilator może kontynuować bez błędów, ale konsolidator nie można rozpoznać wywołania adresu, ponieważ nie ma kodu funkcji lub zmienna zarezerwowanego miejsca. Nie będą widzieć tego błędu, dopóki nie zostanie utworzony wywołanie funkcji, że konsolidator musi zostać rozpoznany.

## <a name="example"></a>Przykład

Wywołanie funkcji w głównym oknie spowoduje LNK2019, ponieważ prototyp umożliwia kompilatorowi wydaje się, że istnieje funkcja.  Konsolidator wykryje, czy nie.

```cpp
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>Przykład

W języku C++ upewnij się, obejmują implementacji określoną funkcję dla klasy i nie tylko prototypu w definicji klasy. Jeśli jest definiowana klasa poza pliku nagłówka, należy uwzględnić nazwę klasy przed funkcji (`Classname::memberfunction`).

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

## <a name="see-also"></a>Zobacz także

[Błąd narzędzi konsolidatora LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)