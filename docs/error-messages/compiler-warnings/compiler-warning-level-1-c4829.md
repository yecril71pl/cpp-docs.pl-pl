---
title: Kompilator ostrzeżenie (poziom 1) C4829
ms.date: 11/04/2016
f1_keywords:
- C4829
helpviewer_keywords:
- C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
ms.openlocfilehash: 1afb29b10352150cac2969849979fb5b5e2b8719
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522562"
---
# <a name="compiler-warning-level-1-c4829"></a>Kompilator ostrzeżenie (poziom 1) C4829

Prawdopodobnie niepoprawne parametry funkcji głównego. Należy wziąć pod uwagę "intmain (Platform::Array\<Platform::String ^ > ^ argv)"

Pewne funkcje, takie jak main, nie można przyjąć odwołania parametrów typu. Gdy kompilacja się powiedzie, obraz wynikowy prawdopodobnie nie będzie działać.

Poniższy przykład spowoduje wygenerowanie C4829:

```
// C4829.cpp
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp
int main(Platform::String ^ s) {}   // C4829
```