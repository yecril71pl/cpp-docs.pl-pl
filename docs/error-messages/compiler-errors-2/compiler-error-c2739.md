---
title: Błąd kompilatora C2739
ms.date: 11/04/2016
f1_keywords:
- C2739
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
ms.openlocfilehash: 18cece8d9630aa93e867329acc7cefea30da3286
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759662"
---
# <a name="compiler-error-c2739"></a>Błąd kompilatora C2739

"number": Wymiary jawnie zarządzane lub tablica WinRT muszą zawierać się w przedziale od 1 do 32

Wymiar tablicy nie ma zakresu od 1 do 32.

Poniższy przykład generuje C2739 i pokazuje, jak to naprawić:

```cpp
// C2739.cpp
// compile with: /clr
int main() {
   array<int, -1>^a;   // C2739
   // try the following line instead
   // array<int, 2>^a;
}
```
