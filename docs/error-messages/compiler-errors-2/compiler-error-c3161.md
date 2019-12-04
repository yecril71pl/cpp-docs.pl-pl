---
title: Błąd kompilatora C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 7315dad7959cdd3b950ed814b13be3867399d332
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761819"
---
# <a name="compiler-error-c3161"></a>Błąd kompilatora C3161

"Interface": zagnieżdżanie klasy, struktury, Unii lub interfejsu w interfejsie jest niedozwolone; Zagnieżdżanie interfejsu w klasie, strukturze lub Unii jest niedozwolone

[__Interface](../../cpp/interface.md) może występować tylko w zakresie globalnym lub w przestrzeni nazw. Klasa, struktura lub Unia nie mogą występować w interfejsie.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3161.

```cpp
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```
