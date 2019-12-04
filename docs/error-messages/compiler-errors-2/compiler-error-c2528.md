---
title: Błąd kompilatora C2528
ms.date: 11/04/2016
f1_keywords:
- C2528
helpviewer_keywords:
- C2528
ms.assetid: 2ea9d583-67a8-4b16-b35f-a50eeffc03c4
ms.openlocfilehash: f8712cfbd34e852cf852cf9758446849d75d8bdc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756269"
---
# <a name="compiler-error-c2528"></a>Błąd kompilatora C2528

"name": wskaźnik do odwołania jest niedozwolony

Nie można zadeklarować wskaźnika do odwołania. Odwołuje się do zmiennej przed zadeklarowaniem wskaźnika.

Poniższy przykład generuje C2528:

```cpp
// C2528.cpp
int i;
int &ir = i;
int & (*irptr) = ir;    // C2528
```
