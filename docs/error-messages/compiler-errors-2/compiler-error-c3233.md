---
title: Błąd kompilatora C3233
ms.date: 11/04/2016
f1_keywords:
- C3233
helpviewer_keywords:
- C3233
ms.assetid: a9210830-1136-4f02-ba41-030c85f93547
ms.openlocfilehash: 110d1ef84ca2f558f597afadadbede61a89da20c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751108"
---
# <a name="compiler-error-c3233"></a>Błąd kompilatora C3233

"Type": parametr typu generycznego jest już ograniczony

Ograniczenie parametru generycznego w więcej niż jednej klauzuli `where` nie jest prawidłowe.

Poniższy przykład generuje C3233:

```cpp
// C3233.cpp
// compile with: /clr /LD

interface struct C {};
interface struct D {};

generic <class T>
where T : C
where T : D
ref class E {};   // C3233
```
