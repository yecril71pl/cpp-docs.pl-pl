---
title: Błąd kompilatora C2867
ms.date: 11/04/2016
f1_keywords:
- C2867
helpviewer_keywords:
- C2867
ms.assetid: 63be26b2-d9ab-4f3d-a8b7-981ce3e4d6b9
ms.openlocfilehash: 66d71d87fbb8e5dce495803f1251565bb14d23f8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212647"
---
# <a name="compiler-error-c2867"></a>Błąd kompilatora C2867

"Identyfikator": nie jest przestrzenią nazw

**`using`** Dyrektywa jest stosowana do elementu innego niż przestrzeń nazw.

Poniższy przykład generuje C2867:

```cpp
// C2867.cpp
// compile with: /c
namespace N {
   class X {};
}
using namespace N::X;   // C2867
```
