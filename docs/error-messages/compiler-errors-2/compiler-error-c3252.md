---
title: Błąd kompilatora C3252
ms.date: 11/04/2016
f1_keywords:
- C3252
helpviewer_keywords:
- C3252
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
ms.openlocfilehash: ee9245fb8eb89b9234e76dc10304b1d05bc1fdcb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164842"
---
# <a name="compiler-error-c3252"></a>Błąd kompilatora C3252

"method": nie można zredukować dostępności wirtualnej metody w zarządzanej lub typu WinRT

Klasa, która implementuje metodę wirtualną z klasy bazowej lub metody w interfejsie nie można zmniejszyć dostępu do tej metody.

Należy pamiętać, że wszystkie metody w interfejsie są publiczne.

Poniższy przykład generuje C3252 i pokazuje, jak go naprawić:

```
// C3252.cpp
// compile with: /clr /c
ref class A {
public:
   virtual void f1() {}
};

ref class B : public A {
// To fix, uncomment the following line:
// public:
   virtual void f1() override sealed {}   // C3252, make this method public
};
```