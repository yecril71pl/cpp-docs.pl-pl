---
title: Błąd kompilatora C3238
ms.date: 11/04/2016
f1_keywords:
- C3238
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
ms.openlocfilehash: d70bb6dac7cb43701b57f3821872e02ab31426dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173317"
---
# <a name="compiler-error-c3238"></a>Błąd kompilatora C3238

"type": typ o tej nazwie już został przesłany dalej do zestawu 'Zestaw'

Typ został zdefiniowany w aplikacji klienckiej, która również jest zdefiniowana za pomocą typu przekazywania składni w przywoływanym zestawie. Nie można zdefiniować obu typów w zakresie aplikacji.

Zobacz [Type Forwarding (C++sposób niezamierzony)](../../extensions/type-forwarding-cpp-cli.md) Aby uzyskać więcej informacji.

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