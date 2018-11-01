---
title: Błąd kompilatora C3909
ms.date: 11/04/2016
f1_keywords:
- C3909
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
ms.openlocfilehash: 435288ba657bd22ba29c6681014ae15baa051cec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636465"
---
# <a name="compiler-error-c3909"></a>Błąd kompilatora C3909

aWinRT lub deklaracji zdarzenie zarządzane musi przypadać w WinRT lub typu zarządzanego

Zdarzenia środowiska uruchomieniowego Windows lub zarządzanych zdarzeń została zadeklarowana w typie natywnym. Aby naprawić ten błąd, należy zadeklarować zdarzenia w typów środowiska wykonawczego Windows lub typami zarządzanymi.

Aby uzyskać więcej informacji, zobacz [zdarzeń](../../windows/event-cpp-component-extensions.md).

Poniższy przykład generuje C3909 i pokazuje, jak go naprawić:

```
// C3909.cpp
// compile with: /clr /c
delegate void H();
class X {
   event H^ E;   // C3909 - use ref class X instead
};

ref class Y {
   static event H^ E {
      void add(H^) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```