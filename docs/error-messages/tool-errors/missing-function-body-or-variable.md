---
title: Brakująca treść funkcji lub zmienna
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 88470272192520e9aa0582fd06ff36a0542803ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647125"
---
# <a name="missing-function-body-or-variable"></a>Brakująca treść funkcji lub zmienna

Po prostu prototypu funkcji kompilator może kontynuować bez błędów, ale konsolidator nie można rozpoznać wywołania adresu, ponieważ nie ma kodu funkcji lub zmienna zarezerwowanego miejsca. Nie będą widzieć tego błędu, dopóki nie zostanie utworzony wywołanie funkcji, że konsolidator musi zostać rozpoznany.

## <a name="example"></a>Przykład

Wywołanie funkcji w głównym oknie spowoduje LNK2019, ponieważ prototyp umożliwia kompilatorowi wydaje się, że istnieje funkcja.  Konsolidator wykryje, czy nie.

```
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>Przykład

W języku C++ upewnij się, obejmują implementacji określoną funkcję dla klasy i nie tylko prototypu w definicji klasy. Jeśli jest definiowana klasa poza pliku nagłówka, należy uwzględnić nazwę klasy przed funkcji (`Classname::memberfunction`).

```
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