---
title: Kompilator ostrzeżenie (poziom 1) C4183 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4183
dev_langs:
- C++
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2753b8fc47de3363c38ed6ee4dedeaf8d085c485
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022439"
---
# <a name="compiler-warning-level-1-c4183"></a>Kompilator ostrzeżenie (poziom 1) C4183

'Identyfikator': Brak typu zwracanego; przyjmuje się, że jest funkcją składową zwracającą "int"

Wewnętrznej definicji funkcji składowej klasy lub struktury nie ma typ zwracany. Ta funkcja elementu członkowskiego przyjęto domyślną zwracany typ `int`.

Poniższy przykład spowoduje wygenerowanie C4183:

```
// C4183.cpp
// compile with: /W1 /c
#pragma warning(disable : 4430)
class MyClass1;
class MyClass2 {
   MyClass1() {};   // C4183
};
```