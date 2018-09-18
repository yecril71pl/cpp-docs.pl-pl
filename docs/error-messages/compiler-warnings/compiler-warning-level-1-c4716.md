---
title: Kompilator ostrzeżenie (poziom 1) C4716 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4716
dev_langs:
- C++
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f7a6fd31ecae4643e947cb4a56897e80010e350
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093405"
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