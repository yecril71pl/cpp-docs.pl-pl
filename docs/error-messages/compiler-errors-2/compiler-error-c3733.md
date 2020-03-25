---
title: Błąd kompilatora C3733
ms.date: 11/04/2016
f1_keywords:
- C3733
helpviewer_keywords:
- C3733
ms.assetid: 0cc1a9fe-1400-4be3-b35a-16435cba7a5a
ms.openlocfilehash: 961aa0caf31d49917f6df67305bc01d465884b68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165902"
---
# <a name="compiler-error-c3733"></a>Błąd kompilatora C3733

"Event": Niewłaściwa składnia określająca zdarzenie COM; Czy pamiętasz "__interface"?

Użyto nieprawidłowej składni dla zdarzenia COM. Aby naprawić ten błąd, Zmień typ zdarzenia lub Popraw składnię, aby zachować zgodność z regułami zdarzeń modelu COM.

Poniższy przykład generuje C3733:

```
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[coclass, event_source(com), // change 'com' to 'native' to resolve
uuid("00000000-0000-0000-0000-000000000001")]
class A
{
   __event void func();   // C3733
};

int main()
{
}
```
