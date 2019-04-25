---
title: Błąd kompilatora C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 22ecc176036308699c3ad7bd8c015836be910073
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174215"
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