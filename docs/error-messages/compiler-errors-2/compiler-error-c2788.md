---
title: Błąd kompilatora C2788
ms.date: 11/04/2016
f1_keywords:
- C2788
helpviewer_keywords:
- C2788
ms.assetid: 8688fc5c-e652-43b4-b407-9c488c76f2db
ms.openlocfilehash: 0025aa5211c2736860bdd30cad4315f63fba9337
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62256896"
---
# <a name="compiler-error-c2788"></a>Błąd kompilatora C2788

'Identyfikator': więcej niż jeden GUID skojarzony z tym obiektem

[__Uuidof](../../cpp/uuidof-operator.md) operator ma typ zdefiniowany przez użytkownika z identyfikatorem GUID dołączone lub obiektu takiego typu zdefiniowanego przez użytkownika. Ten błąd występuje, gdy argument jest obiekt o wiele identyfikatorów GUID.

Poniższy przykład spowoduje wygenerowanie C2788:

```
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