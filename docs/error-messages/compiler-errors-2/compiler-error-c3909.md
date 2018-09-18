---
title: Błąd kompilatora C3909 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3909
dev_langs:
- C++
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bb3526f537a2eceb006f6af9e9b0faba44bf9cf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058708"
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