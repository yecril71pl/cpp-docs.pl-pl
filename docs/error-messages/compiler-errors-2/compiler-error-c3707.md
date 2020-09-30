---
title: Błąd kompilatora C3707
ms.date: 11/04/2016
f1_keywords:
- C3707
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
ms.openlocfilehash: a09bf080c72e154a37cec5cdb75e714c12dd7150
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507981"
---
# <a name="compiler-error-c3707"></a>Błąd kompilatora C3707

"Function": Metoda dispinterface musi mieć identyfikator DISPID

Jeśli używasz `dispinterface` metody, musisz ją przypisać `dispid` . Aby naprawić ten błąd, należy przypisać `dispid` do `dispinterface` metody, na przykład przez usunięcie komentarza `id` atrybutu metody w poniższym przykładzie. Aby uzyskać więcej informacji, zobacz atrybuty [dispinterface](../../windows/attributes/dispinterface.md) i [ID](../../windows/attributes/id.md).

Poniższy przykład generuje C3707:

```cpp
// C3707.cpp
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(name="xx")];
[dispinterface]
__interface IEvents : IDispatch
{
   HRESULT event1([in] int i);   // C3707
   // try the following line instead
   // [id(1)] HRESULT event1([in] int i);
};

int main() {
}
```
