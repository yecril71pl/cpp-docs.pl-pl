---
title: Błąd kompilatora C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 22ecc176036308699c3ad7bd8c015836be910073
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501663"
---
# <a name="compiler-error-c3161"></a>Błąd kompilatora C3161

"interface": zagnieżdżanie klasy, struktury, Unii lub interfejsu w interfejsie jest niedozwolone; Zagnieżdżanie interfejsu w klasy, struktury lub Unii jest niedozwolony

[__Interface](../../cpp/interface.md) może wystąpić tylko w zakresie globalnym lub przestrzeni nazw. Klasy, struktury lub Unii nie są wyświetlane w interfejsie.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3161.

```
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```