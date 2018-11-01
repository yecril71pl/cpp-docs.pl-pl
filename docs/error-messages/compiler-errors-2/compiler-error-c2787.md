---
title: Błąd kompilatora C2787
ms.date: 11/04/2016
f1_keywords:
- C2787
helpviewer_keywords:
- C2787
ms.assetid: 34cb57e6-cafe-4ce7-bcc6-53d194629bd0
ms.openlocfilehash: 656fcd8a1a0429546189de8c3f01ab928c6333ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587788"
---
# <a name="compiler-error-c2787"></a>Błąd kompilatora C2787

'Identyfikator': Brak GUID nie został skojarzony z tym obiektem

[__Uuidof](../../cpp/uuidof-operator.md) operator ma typ zdefiniowany przez użytkownika z identyfikatorem GUID dołączone lub obiektu takiego typu zdefiniowanego przez użytkownika. Ten błąd występuje, gdy argument jest typu zdefiniowanego przez użytkownika, za pomocą żaden identyfikator GUID.

Poniższy przykład spowoduje wygenerowanie C2787:

```
// C2787.cpp
#include <windows.h>
struct F {};

struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) F2;

int main() {
   __uuidof(F);   // C2787
   __uuidof(F2);   // OK
}
```