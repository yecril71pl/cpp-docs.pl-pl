---
title: Błąd kompilatora C3896
ms.date: 11/04/2016
f1_keywords:
- C3896
helpviewer_keywords:
- C3896
ms.assetid: eb8be0f6-5b4e-4d71-8285-8a2a94f8ba29
ms.openlocfilehash: 32aed1dfd957035cdd60fa97bd9ec534de03cb06
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547957"
---
# <a name="compiler-error-c3896"></a>Błąd kompilatora C3896

"członek": niewłaściwy inicjator: ten literał składowej danych może być inicjowane tylko z "nullptr"

A [literału](../../windows/literal-cpp-component-extensions.md) element członkowski danych został niepoprawnie zainicjowany.  Zobacz [nullptr](../../windows/nullptr-cpp-component-extensions.md) Aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C3896:

```
// C3896.cpp
// compile with: /clr /c
ref class R{};

value class V {
   literal R ^ r = "test";   // C3896
   literal R ^ r2 = nullptr;   // OK
};
```