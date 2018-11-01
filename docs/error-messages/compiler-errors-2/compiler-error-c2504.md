---
title: Błąd kompilatora C2504
ms.date: 11/04/2016
f1_keywords:
- C2504
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
ms.openlocfilehash: 8f428699aa14cbd1f021a57ed8dcabefa8b24c16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444394"
---
# <a name="compiler-error-c2504"></a>Błąd kompilatora C2504

"class": klasa bazowa niezdefiniowana

Klasa bazowa jest zadeklarowana, ale nigdy nie jest zdefiniowany.  Możliwe przyczyny:

1. Brak pliku dołączenia.

1. Zewnętrzne klasy bazowej nie jest zadeklarowana za pomocą [extern](../../cpp/using-extern-to-specify-linkage.md).

Poniższy przykład spowoduje wygenerowanie C2504:

```
// C2504.cpp
// compile with: /c
class A;
class B : public A {};   // C2504
```

OK

```
class C{};
class D : public C {};
```