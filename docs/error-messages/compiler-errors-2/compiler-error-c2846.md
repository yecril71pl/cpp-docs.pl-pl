---
title: Błąd kompilatora C2846
ms.date: 11/04/2016
f1_keywords:
- C2846
helpviewer_keywords:
- C2846
ms.assetid: bc090ec2-5410-4112-9ec6-261325374375
ms.openlocfilehash: eef558301ce2d623ef78aab40a7a054cd73037df
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750614"
---
# <a name="compiler-error-c2846"></a>Błąd kompilatora C2846

"Konstruktor": interfejs nie może mieć konstruktora

C++ [Interfejs](../../cpp/interface.md) wizualizacji nie może mieć konstruktora.

Poniższy przykład generuje C2846:

```cpp
// C2846.cpp
// compile with: /c
__interface C {
   C();   // C2846 constructor not allowed in an interface
};
```
