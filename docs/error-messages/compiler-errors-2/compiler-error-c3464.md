---
title: Błąd kompilatora C3464
ms.date: 11/04/2016
f1_keywords:
- C3464
helpviewer_keywords:
- C3464
ms.assetid: 0ede05dc-4486-4921-8e8c-78ab5a2e09c5
ms.openlocfilehash: b21810d6df1fbfaf5ea94d9515487b16d00af548
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58775299"
---
# <a name="compiler-error-c3464"></a>Błąd kompilatora C3464

Nie można przesłać dalej typu zagnieżdżonego "type"

Przekazywanie dalej typu nie działa dla typów zagnieżdżonych.

Aby uzyskać więcej informacji, zobacz [przekazywania dalej typów (C + +/ CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład tworzy składnik.

```
// C3464.cpp
// compile with: /LD /clr
public ref class R {
public:
   ref class N {};
};
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3464.

```
// C3464_b.cpp
// compile with: /clr /c
#using "C3464.dll"
[assembly:TypeForwardedTo(R::N::typeid)];   // C3464
[assembly:TypeForwardedTo(R::typeid)];   // OK
```