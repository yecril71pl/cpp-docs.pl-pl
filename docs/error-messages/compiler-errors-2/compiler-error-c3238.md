---
title: Błąd kompilatora C3238
ms.date: 11/04/2016
f1_keywords:
- C3238
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
ms.openlocfilehash: d81fd0fb3612a8c22fa6365aa7fc6dddb89cf120
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481162"
---
# <a name="compiler-error-c3238"></a>Błąd kompilatora C3238

"type": typ o tej nazwie już został przesłany dalej do zestawu 'Zestaw'

Typ został zdefiniowany w aplikacji klienckiej, która również jest zdefiniowana za pomocą typu przekazywania składni w przywoływanym zestawie. Nie można zdefiniować obu typów w zakresie aplikacji.

Zobacz [przekazywania dalej typów (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład tworzy zestaw, który zawiera typ, który został przekazany z innego zestawu.

```
// C3238.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>Przykład

Poniższy przykład tworzy zestaw, który zawiera definicję typu, ale zawiera nie tylko typ przekazywania składni.

```
// C3238_b.cpp
// compile with: /clr /LD
#using "C3238.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3238.

```
// C3238_c.cpp
// compile with: /clr /c
// C3238 expected
// Delete the following line to resolve.
#using "C3238_b.dll"
public ref class R {};
```