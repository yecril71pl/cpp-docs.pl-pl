---
title: Błąd kompilatora C2499
ms.date: 11/04/2016
f1_keywords:
- C2499
helpviewer_keywords:
- C2499
ms.assetid: b323ff4d-b3c1-4bfd-b052-ae7292d53222
ms.openlocfilehash: 645dd3923e65240de17803a8831a0223ff0e1656
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50427823"
---
# <a name="compiler-error-c2499"></a>Błąd kompilatora C2499

"class": klasa nie może być siebie klasą bazową

Podjęto próbę określenia klasy, który jest definiowany jako klasę bazową.

Poniższy przykład spowoduje wygenerowanie C2499:

```
// C2499.cpp
// compile with: /c
class CMyClass : public CMyClass {};   // C2499
class CMyClass{};   // OK
```