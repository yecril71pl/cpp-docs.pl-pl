---
title: Błąd kompilatora C2867
ms.date: 11/04/2016
f1_keywords:
- C2867
helpviewer_keywords:
- C2867
ms.assetid: 63be26b2-d9ab-4f3d-a8b7-981ce3e4d6b9
ms.openlocfilehash: 42b931d208000cc35e65c7bff9c20901cef24713
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755060"
---
# <a name="compiler-error-c2867"></a>Błąd kompilatora C2867

"Identyfikator": nie jest przestrzenią nazw

Dyrektywa `using` jest stosowana do elementu innego niż przestrzeń nazw.

Poniższy przykład generuje C2867:

```cpp
// C2867.cpp
// compile with: /c
namespace N {
   class X {};
}
using namespace N::X;   // C2867
```
