---
title: Kompilator ostrzeżenie (poziom 1) C4716
ms.date: 11/04/2016
f1_keywords:
- C4716
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
ms.openlocfilehash: 5ec0aea543053d699db7483df7dd7ea91b3af715
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594548"
---
# <a name="compiler-warning-level-1-c4716"></a>Kompilator ostrzeżenie (poziom 1) C4716

'Funkcja' musi zwracać wartość

Daną funkcję nie zwrócił wartość.

Działa tylko z typem zwrotnym void może użyć polecenie return bez towarzyszącego wartości zwracanej.

Niezdefiniowaną wartość jest zwracany, gdy ta funkcja jest wywoływana.

To ostrzeżenie zostanie automatycznie podwyższony do błędu. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md).

Poniższy przykład spowoduje wygenerowanie C4716:

```
// C4716.cpp
// compile with: /c /W1
// C4716 expected
#pragma warning(default:4716)
int test() {
   // uncomment the following line to resolve
   // return 0;
}
```