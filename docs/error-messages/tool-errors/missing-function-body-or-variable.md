---
title: Brak treści funkcji lub zmienna | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a1337cf936d986c038aacc355490f13e5f0c2d8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088454"
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