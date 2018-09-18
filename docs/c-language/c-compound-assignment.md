---
title: Przydział złożony języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4450682abbb5efd739b5eb08d228b4c55d00ec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029328"
---
# <a name="c-compound-assignment"></a>Przydział złożony języka C

Operatory przypisania złożone łączyć operator przypisania prostego za pomocą innego operatora binarnego. Operatory przypisania złożone wykonać operację określoną przez operator dodatkowe, a następnie przypisz wynik do lewy operand. Na przykład, wyrażenie przypisanie złożone, takich jak

> *wyrażenie1* **+=** *wyrażenie2*

może być rozumiany jako

> *wyrażenie1* **=** *wyrażenie1* **+** *wyrażenie2*

Jednak przypisanie złożone wyrażenie nie jest odpowiednikiem rozszerzoną wersję, ponieważ przypisanie złożone wyrażenie *wyrażenie1* tylko raz, podczas gdy ocenia rozszerzoną wersję  *wyrażenie1* dwa razy: operacja dodawania i operacji przypisania.

Argumenty operacji operatora przypisania złożone musi być typu całkowitego lub zmiennoprzecinkowego. Każdy operator przypisania złożone wykonuje konwersje, że odpowiedniego operatora binarnego wykonuje i ogranicza możliwość użycia typy argumentów. Przypisania dodawania (`+=`) i odejmowanie i przypisanie (**-=**) operatorzy mogą też istnieć lewy operand typu wskaźnika, w którym przypadku prawostronny operand musi być typu całkowitego. Wynik operacji przypisania złożony ma wartość i typ operandu po lewej stronie.

```C
#define MASK 0xff00

n &= MASK;
```

W tym przykładzie operacji bitowej włączne i odbywa się na `n` i `MASK`, a wynik jest przypisany do `n`. Stała manifestu `MASK` jest zdefiniowana za pomocą [#define](../preprocessor/hash-define-directive-c-cpp.md) dyrektywy preprocesora.

## <a name="see-also"></a>Zobacz też

[Operatory przypisania w języku C](../c-language/c-assignment-operators.md)