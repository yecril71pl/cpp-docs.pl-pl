---
title: Błąd kompilatora C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: a6ffcb13d04f3c7c5ac62e147a2b6b2b305e11e1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218172"
---
# <a name="compiler-error-c2833"></a>Błąd kompilatora C2833

> "operator *-name*" nie jest rozpoznanym operatorem lub typem

Po słowie **`operator`** musi następować *nazwa operatora* , który ma zostać przesłonięty, lub typ, który ma zostać przekształcony.

Aby uzyskać listę operatorów, które można zdefiniować w typie zarządzanym, zobacz [Operatory zdefiniowane przez użytkownika](../../dotnet/user-defined-operators-cpp-cli.md).

Poniższy przykład generuje C2833:

```cpp
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```
