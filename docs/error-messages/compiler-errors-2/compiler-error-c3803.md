---
title: Błąd kompilatora C3803
ms.date: 11/04/2016
f1_keywords:
- C3803
helpviewer_keywords:
- C3803
ms.assetid: bad5fb9a-ed9a-4c15-96e7-cf06e200a50d
ms.openlocfilehash: f6c255ec18d6dcf94f3ec022f09b173c2c66a1dd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565090"
---
# <a name="compiler-error-c3803"></a>Błąd kompilatora C3803

"właściwość": właściwość ma typ, który nie jest zgodny z jednym z jego metody dostępu "akcesor"

Typ właściwości zdefiniowane za pomocą [właściwość](../../cpp/property-cpp.md) jest niezgodny z typem zwracanym dla jednej z jej funkcji dostępu.

Poniższy przykład spowoduje wygenerowanie C3803:

```
// C3803.cpp
struct A
{
   __declspec(property(get=GetIt)) int i;
   char GetIt()
   {
      return 0;
   }

   /*
   // try the following definition instead
   int GetIt()
   {
      return 0;
   }
   */
}; // C3803

int main()
{
}
```