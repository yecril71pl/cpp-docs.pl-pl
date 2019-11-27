---
title: Ostrzeżenie kompilatora (poziom 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: 80794d270b40a8f40d44630da70455c015158423
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541240"
---
# <a name="compiler-warning-level-4-c4100"></a>Ostrzeżenie kompilatora (poziom 4) C4100

"Identyfikator": parametr formalny, do którego nie istnieją odwołania

Parametr formalny nie jest przywoływany w treści funkcji. Parametr bez odwołania jest ignorowany.

C4100 może być również wystawiony, gdy kod wywołuje destruktor dla nieodwołanego parametru typu pierwotnego.  Jest to ograniczenie kompilatora firmy Microsoft C++ .

Poniższy przykład generuje C4100:

```cpp
// C4100.cpp
// compile with: /W4
void func(int i) {   // C4100, delete the unreferenced parameter to
                     //resolve the warning
   // i;   // or, add a reference like this
}

int main()
{
   func(1);
}
```