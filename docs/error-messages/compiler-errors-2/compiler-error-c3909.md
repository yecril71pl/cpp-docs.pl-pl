---
title: Błąd kompilatora C3909
ms.date: 11/04/2016
f1_keywords:
- C3909
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
ms.openlocfilehash: 69613a1058bd5178ea4c03931664dd00bad7a101
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748999"
---
# <a name="compiler-error-c3909"></a>Błąd kompilatora C3909

aWinRT lub Deklaracja zdarzenia zarządzanego musi następować w typie WinRT lub zarządzanym

Zdarzenie środowisko wykonawcze systemu Windows lub zdarzenie zarządzane zostało zadeklarowane w typie natywnym. Aby naprawić ten błąd, zadeklaruj zdarzenia w typach środowisko wykonawcze systemu Windows lub typach zarządzanych.

Aby uzyskać więcej informacji, zobacz [zdarzenie](../../extensions/event-cpp-component-extensions.md).

Poniższy przykład generuje C3909 i pokazuje, jak to naprawić:

```cpp
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
