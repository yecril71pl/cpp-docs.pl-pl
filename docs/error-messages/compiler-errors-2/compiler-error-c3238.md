---
title: Błąd kompilatora C3238
ms.date: 11/04/2016
f1_keywords:
- C3238
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
ms.openlocfilehash: 1f238a3be27023c755544438166aae1b2b2967d3
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741986"
---
# <a name="compiler-error-c3238"></a>Błąd kompilatora C3238

"Type": typ o tej nazwie został już przekazany do zestawu "Assembly"

Typ został zdefiniowany w aplikacji klienckiej, która jest również zdefiniowana, za pomocą składni przekazywania typów, w przywoływanym zestawie. Oba typy nie mogą być zdefiniowane w zakresie aplikacji.

Aby uzyskać więcej informacji, zobacz [przekazywanie dalej typu (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md) .

## <a name="examples"></a>Przykłady

Poniższy przykład tworzy zestaw, który zawiera typ, który został przesłany dalej z innego zestawu.

```cpp
// C3238.cpp
// compile with: /clr /LD
public ref class R {};
```

Poniższy przykład tworzy zestaw, który służy do zawiera definicję typu, ale nie tylko zawiera składnię przekazywania typów.

```cpp
// C3238_b.cpp
// compile with: /clr /LD
#using "C3238.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

Poniższy przykład generuje C3238.

```cpp
// C3238_c.cpp
// compile with: /clr /c
// C3238 expected
// Delete the following line to resolve.
#using "C3238_b.dll"
public ref class R {};
```
