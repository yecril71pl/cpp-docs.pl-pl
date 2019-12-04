---
title: Błąd kompilatora C2086
ms.date: 11/04/2016
f1_keywords:
- C2086
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
ms.openlocfilehash: 417763e8c26918d3cd83702b283244d1c13d9d1f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735752"
---
# <a name="compiler-error-c2086"></a>Błąd kompilatora C2086

"Identyfikator": zmiana definicji

Identyfikator jest zdefiniowany więcej niż raz lub kolejna deklaracja różni się od poprzedniej.

C2086 może być również wynikiem kompilowania przyrostowego dla przywoływanego C# zestawu. Skompiluj ponownie C# zestaw, aby rozwiązać ten problem.

Poniższy przykład generuje C2086:

```cpp
// C2086.cpp
main() {
  int a;
  int a;   // C2086 not an error in ANSI C
}
```
