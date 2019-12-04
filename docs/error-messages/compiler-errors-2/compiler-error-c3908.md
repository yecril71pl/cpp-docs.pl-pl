---
title: Błąd kompilatora C3908
ms.date: 11/04/2016
f1_keywords:
- C3908
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
ms.openlocfilehash: 2b57f3346427ff548d11fe776e909eca99433a81
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749038"
---
# <a name="compiler-error-c3908"></a>Błąd kompilatora C3908

poziom dostępu mniej restrykcyjny niż "konstrukcja"

Metoda dostępu do właściwości (get lub Set) nie może mieć mniej restrykcyjnego dostępu niż określony we właściwości.  Podobnie, w przypadku metod metody dostępu do zdarzeń.

Aby uzyskać więcej informacji, zobacz [Właściwości](../../extensions/property-cpp-component-extensions.md) i [zdarzenia](../../extensions/event-cpp-component-extensions.md).

Poniższy przykład generuje C3908:

```cpp
// C3908.cpp
// compile with: /clr
ref class X {
protected:
   property int i {
   public:   // C3908 property i is protected
      int get();
   private:
      void set(int);   // OK more restrictive
   };
};
```
