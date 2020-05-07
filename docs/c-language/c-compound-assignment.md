---
title: Przydział złożony języka C
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
ms.openlocfilehash: 39a9391e2a62a59c5e7fd7937c1f3d12509b76ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327902"
---
# <a name="c-compound-assignment"></a>Przydział złożony języka C

Operatory przypisania złożonego łączą operator przypisania prostego z innym operatorem binarnym. Operatory przypisania złożonego wykonują operacje określone przez operator dodatkowy, a następnie przypisują wynik do lewego operandu. Na przykład wyrażenie przypisania złożonego, takie jak

> *wyrażenie1* **+=** *wyrażenie2*

można zrozumieć jako

> *wyrażenie1* **=** *expression1* wyrażenie1 **+** *wyrażenie2*

Jednak wyrażenie przypisania złożonego nie jest odpowiednikiem rozwiniętej wersji, ponieważ wyrażenie przypisania złożonego szacuje wartość *wyrażenie1* tylko raz, podczas gdy rozszerzona wersja szacuje wartość *wyrażenie1* dwa razy: w operacji dodawania i w operacji przypisania.

Argumenty operacji operatora przypisania złożonego muszą być typu całkowitego lub zmiennoprzecinkowego. Każdy operator przypisania złożonego wykonuje konwersje, które są wykonywane przez odpowiedni operator binarny i odpowiednio ogranicza typy argumentów. Operatory dodawania/przypisywania (`+=`) i odejmowania —**-=** przypisanie () mogą także mieć lewy operand typu wskaźnik, w tym przypadku prawy operand musi być typu całkowitego. Wynikiem operacji przypisania złożonego jest wartość i typ argumentu operacji po lewej stronie.

```C
#define MASK 0xff00

n &= MASK;
```

W tym przykładzie operacje bitowe i łącznie są wykonywane w systemach `n` i `MASK`, a wynik jest przypisany do. `n` Stała `MASK` manifestu jest definiowana za pomocą dyrektywy preprocesora [#define](../preprocessor/hash-define-directive-c-cpp.md) .

## <a name="see-also"></a>Zobacz też

[Operatory przypisania w języku C](../c-language/c-assignment-operators.md)
