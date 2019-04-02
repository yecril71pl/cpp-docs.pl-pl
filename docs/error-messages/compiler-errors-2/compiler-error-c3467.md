---
title: Błąd kompilatora C3467
ms.date: 11/04/2016
f1_keywords:
- C3467
helpviewer_keywords:
- C3467
ms.assetid: e2b844d0-4920-412f-99fd-cd8051c4aa41
ms.openlocfilehash: 70375950543b9525fca10fff3084c923095fa35e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780759"
---
# <a name="compiler-error-c3467"></a>Błąd kompilatora C3467

"type": ten typ został już przekazany

Kompilator znaleziono więcej niż jedna deklaracja typu do przodu dla tego samego typu. Dozwolone jest tylko jedna deklaracja według typu.

Aby uzyskać więcej informacji, zobacz [przekazywania dalej typów (C + +/ CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład tworzy składnik.

```
// C3467.cpp
// compile with: /LD /clr
public ref class R {};
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3467.

```
// C3467_b.cpp
// compile with: /clr /c
#using "C3467.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
[ assembly:TypeForwardedTo(R::typeid) ];   // C3467
```