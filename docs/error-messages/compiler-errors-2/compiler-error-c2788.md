---
title: Błąd kompilatora C2788
ms.date: 11/04/2016
f1_keywords:
- C2788
helpviewer_keywords:
- C2788
ms.assetid: 8688fc5c-e652-43b4-b407-9c488c76f2db
ms.openlocfilehash: a708e711fd086d31ecd5e8cc9c35679571af48c4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739574"
---
# <a name="compiler-error-c2788"></a>Błąd kompilatora C2788

"Identyfikator": więcej niż jeden identyfikator GUID skojarzony z tym obiektem

Operator [__uuidof](../../cpp/uuidof-operator.md) przyjmuje zdefiniowany przez użytkownika typ z DOŁĄCZONYm identyfikatorem GUID lub obiektem takiego typu zdefiniowanego przez użytkownika. Ten błąd występuje, gdy argument jest obiekt z wieloma identyfikatorami GUID.

Poniższy przykład generuje C2788:

```cpp
// C2788.cpp
#include <windows.h>
struct __declspec(uuid("00000001-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000002-0000-0000-0000-000000000000}")) B {};
template <class T, class U> class MyClass {};

typedef MyClass<A,B> MyBadClass;
typedef MyClass<A,A> MyGoodClass;

int main() {
   __uuidof(MyBadClass);    // C2788
   // try the following line instead
   __uuidof(MyGoodClass);
}
```
