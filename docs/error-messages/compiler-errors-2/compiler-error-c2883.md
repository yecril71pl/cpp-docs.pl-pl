---
title: Błąd kompilatora C2883
ms.date: 11/04/2016
f1_keywords:
- C2883
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
ms.openlocfilehash: fcd97a2f362e50ec856e53da2603c29e07595670
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233473"
---
# <a name="compiler-error-c2883"></a>Błąd kompilatora C2883

"name": deklaracja funkcji powoduje konflikt z elementem "identifier" wprowadzonym za pomocą deklaracji using

Podjęto próbę zdefiniowania funkcji więcej niż jeden raz. Pierwsza definicja została wykonana z przestrzeni nazw z **`using`** deklaracją. Druga była definicją lokalną.

Poniższy przykład generuje C2883:

```cpp
// C2883.cpp
namespace A {
   void z(int);
}

int main() {
   using A::z;
   void z(int);   // C2883  z is already defined
}
```
