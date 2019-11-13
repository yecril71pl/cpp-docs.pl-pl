---
title: Ostrzeżenie kompilatora (poziom 1) C4606
ms.date: 11/04/2016
f1_keywords:
- C4606
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
ms.openlocfilehash: d36031aa9a831d4669d796d8a40292e2d6ba15a8
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964975"
---
# <a name="compiler-warning-level-1-c4606"></a>Ostrzeżenie kompilatora (poziom 1) C4606

Ostrzeżenie \#pragma: zignorowano element "warning_number"; Ostrzeżenia analizy kodu nie są skojarzone z poziomami ostrzeżeń

W przypadku ostrzeżeń dotyczących analizy kodu tylko `error`, `once`i `default` są obsługiwane przez pragmę [ostrzeżenia](../../preprocessor/warning.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C4606.

```cpp
// C4606.cpp
// compile with: /c /W1
#pragma warning(1: 6001)   // C4606
#pragma warning(once: 6001)   // OK
```