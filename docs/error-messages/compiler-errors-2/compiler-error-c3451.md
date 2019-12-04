---
title: Błąd kompilatora C3451
ms.date: 11/04/2016
f1_keywords:
- C3451
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
ms.openlocfilehash: 2e0122dd53ba5318077dd33f22a07492c52db26b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756217"
---
# <a name="compiler-error-c3451"></a>Błąd kompilatora C3451

"Attribute": nie można zastosować niezarządzanego atrybutu do "Type"

Nie C++ można zastosować atrybutu do typu CLR. Aby uzyskać więcej informacji, zobacz [ C++ odwołania do atrybutów](../../windows/attributes/attributes-alphabetical-reference.md) .

Aby uzyskać więcej informacji, zobacz [atrybuty zdefiniowane przez użytkownika](../../extensions/user-defined-attributes-cpp-component-extensions.md).

Ten błąd może zostać wygenerowany w wyniku działania kompilatora, który został wykonany dla programu Visual Studio 2005: atrybut [UUID](../../windows/uuid-cpp-attributes.md) nie jest już dozwolony w atrybucie zdefiniowanym przez użytkownika przy użyciu programowania środowiska CLR. Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.GuidAttribute>.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3451.

```cpp
// C3451.cpp
// compile with: /clr /c
using namespace System;
[ attribute(AttributeTargets::All) ]
public ref struct MyAttr {};

[ MyAttr, helpstring("test") ]   // C3451
// try the following line instead
// [ MyAttr ]
public ref struct ABC {};
```
