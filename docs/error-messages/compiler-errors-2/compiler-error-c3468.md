---
title: Compiler Error C3468
ms.date: 11/04/2016
f1_keywords:
- C3468
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
ms.openlocfilehash: e3870fa21e2b4a932937edd49091980406a5ff0d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173187"
---
# <a name="compiler-error-c3468"></a>Compiler Error C3468

"type": można tylko przekazać dalej typ do zestawu:

"`file`" nie jest zestawem

Może być przekazywany tylko typy w zestawie.

Aby uzyskać więcej informacji, zobacz [Type Forwarding (C++sposób niezamierzony)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład tworzy moduł.

```
// C3468.cpp
// compile with: /LN /clr
public ref class R {};
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3468.

```
// C3468_b.cpp
// compile with: /clr /c
#using "C3468.netmodule"
[ assembly:TypeForwardedTo(R::typeid) ];   // C3468
```