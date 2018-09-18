---
title: Kompilator ostrzeżenie (poziom 1) C4033 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4033
dev_langs:
- C++
helpviewer_keywords:
- C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35df279ef7611a62ced5cb6291bdf17331850f0c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102687"
---
# <a name="compiler-warning-level-1-c4033"></a>Kompilator ostrzeżenie (poziom 1) C4033

'Funkcja' musi zwracać wartość

Funkcja nie zwraca wartości. Niezdefiniowaną wartość jest zwracana.

Funkcje, które używają `return` bez zwracana wartość musi być zadeklarowany jako typ `void`.

Ten błąd jest dla kodu języka C.

Poniższy przykład spowoduje wygenerowanie C4033:

```
// C4033.c
// compile with: /W1 /LD
int test_1(int x)   // C4033 expected
{
   if (x)
   {
      return;   // C4033
   }
}
```