---
title: Błąd kompilatora C3846
ms.date: 11/04/2016
f1_keywords:
- C3846
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
ms.openlocfilehash: a4c51ccfc724cf8309044812b287677f0f1a2ff0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754904"
---
# <a name="compiler-error-c3846"></a>Błąd kompilatora C3846

"symbol": nie można zaimportować symbolu z "Assembly2": ponieważ "symbol" został już zaimportowany z innego zestawu "assembly1"

Nie można zaimportować symbolu z przywoływanego zestawu, ponieważ został on poprzednio zaimportowany z przywoływanego zestawu.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3846:

```cpp
// C3846a.cpp
// compile with: /LD /clr
public ref struct G
{
};
```

A następnie Skompiluj:

```cpp
// C3846b.cpp
// compile with: /clr
#using "c3846a.dll"
#using "c3846a.obj"   // C3846

int main()
{
}
```
