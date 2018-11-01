---
title: Błąd kompilatora C3388
ms.date: 11/04/2016
f1_keywords:
- C3388
helpviewer_keywords:
- C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
ms.openlocfilehash: 1f6e51542cc852543d648f9f94a964ae0cab3b30
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512699"
---
# <a name="compiler-error-c3388"></a>Błąd kompilatora C3388

"type": niedozwolone jako ograniczenie, przy założeniu "ref class" Aby kontynuować analizowanie

W typie podstawowym określono ograniczenie, ale ograniczenie nie został poprawnie określony. Zobacz [ograniczenia dotyczące parametrów typu ogólnego (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3388.

```
// C3388.cpp
// compile with: /clr /c
interface class AA {};

generic <class T>
where T : interface class   // C3388
ref class C {};

// OK
generic <class T>
where T : AA
ref class D {};
```