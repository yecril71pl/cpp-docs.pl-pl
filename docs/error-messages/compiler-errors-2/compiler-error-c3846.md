---
title: Błąd kompilatora C3846
ms.date: 11/04/2016
f1_keywords:
- C3846
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
ms.openlocfilehash: 788f03e4364404ad5c30b7edcba8b743c7f201ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651220"
---
# <a name="compiler-error-c3846"></a>Błąd kompilatora C3846

'symbol': nie można zaimportować symbolu z "assembly2": ponieważ "symbol" został już zaimportowany z innego zestawu "assembly1"

Nie można zaimportować symbolu z przywoływanego zestawu, ponieważ nie zostały wcześniej zaimportowane z przywoływanego zestawu.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3846:

```
// C3846a.cpp
// compile with: /LD /clr
public ref struct G
{
};
```

A następnie skompilować to:

```
// C3846b.cpp
// compile with: /clr
#using "c3846a.dll"
#using "c3846a.obj"   // C3846

int main()
{
}
```
