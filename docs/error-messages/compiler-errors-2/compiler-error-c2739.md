---
title: Błąd kompilatora C2739
ms.date: 11/04/2016
f1_keywords:
- C2739
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
ms.openlocfilehash: f7e7b20f64c8975e747fe84138cbcb18c3fd14fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258027"
---
# <a name="compiler-error-c2739"></a>Błąd kompilatora C2739

"numer": jawna zarządzane lub wymiary tablicy WinRT musi należeć do zakresu od 1 do 32

Wymiar tablicy nie od 1 do 32.

Poniższy przykład generuje C2739 i pokazuje, jak go naprawić:

```
// C2739.cpp
// compile with: /clr
int main() {
   array<int, -1>^a;   // C2739
   // try the following line instead
   // array<int, 2>^a;
}
```