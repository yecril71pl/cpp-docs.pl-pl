---
title: Kompilator ostrzeżenie (poziom 1) C4829
ms.date: 11/04/2016
f1_keywords:
- C4829
helpviewer_keywords:
- C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
ms.openlocfilehash: ace409cee05650e0dbfbcdd32cd15e85f8dbf006
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594171"
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