---
title: Błąd kompilatora C3469
ms.date: 11/04/2016
f1_keywords:
- C3469
helpviewer_keywords:
- C3469
ms.assetid: e23b0e5c-c704-4e67-a868-bf02c2055d85
ms.openlocfilehash: 7ae0b7b779749a9787601a6046eadd80c2ba49d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571070"
---
# <a name="compiler-error-c3469"></a>Błąd kompilatora C3469

"type": nie można przesłać dalej klasy ogólnej

Przekazywanie dalej typu nie można użyć dla klasy generycznej.

Aby uzyskać więcej informacji, zobacz [przekazywania dalej typów (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład tworzy składnik.

```
// C3469.cpp
// compile with: /clr /LD
generic<typename T>
public ref class GR {};

public ref class GR2 {};
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3466.

```
// C3469_b.cpp
// compile with: /clr /c
#using "C3469.dll"
[assembly:TypeForwardedTo(GR::typeid)];   // C3469
[assembly:TypeForwardedTo(GR2::typeid)];   // OK
```