---
title: Przydział złożony języka C
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
ms.openlocfilehash: 39a9391e2a62a59c5e7fd7937c1f3d12509b76ad
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148767"
---
# <a name="c-compound-assignment"></a>Przydział złożony języka C

Operatory przypisania złożone łączyć operator przypisania prostego za pomocą innego operatora binarnego. Operatory przypisania złożone wykonać operację określoną przez operator dodatkowe, a następnie przypisz wynik do lewy operand. Na przykład, wyrażenie przypisanie złożone, takich jak

> *expression1* **+=** *expression2*

może być rozumiany jako

> *expression1* **=** *expression1* **+** *expression2*

Jednak przypisanie złożone wyrażenie nie jest odpowiednikiem rozszerzoną wersję, ponieważ przypisanie złożone wyrażenie *wyrażenie1* tylko raz, podczas gdy ocenia rozszerzoną wersję  *wyrażenie1* dwa razy: operacja dodawania i operacji przypisania.

Argumenty operacji operatora przypisania złożone musi być typu całkowitego lub zmiennoprzecinkowego. Każdy operator przypisania złożone wykonuje konwersje, że odpowiedniego operatora binarnego wykonuje i ogranicza możliwość użycia typy argumentów. Przypisania dodawania (`+=`) i odejmowanie i przypisanie (**-=**) operatorzy mogą też istnieć lewy operand typu wskaźnika, w którym przypadku prawostronny operand musi być typu całkowitego. Wynik operacji przypisania złożony ma wartość i typ operandu po lewej stronie.

```C
#define MASK 0xff00

n &= MASK;
```

W tym przykładzie operacji bitowej włączne i odbywa się na `n` i `MASK`, a wynik jest przypisany do `n`. Stała manifestu `MASK` jest zdefiniowana za pomocą [#define](../preprocessor/hash-define-directive-c-cpp.md) dyrektywy preprocesora.

## <a name="see-also"></a>Zobacz także

[Operatory przypisania w języku C](../c-language/c-assignment-operators.md)
