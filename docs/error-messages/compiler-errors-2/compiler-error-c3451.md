---
title: Błąd kompilatora C3451
ms.date: 11/04/2016
f1_keywords:
- C3451
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
ms.openlocfilehash: 5ef4352101541391a7cda88471fbaa6aeae4ffb4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328721"
---
# <a name="compiler-error-c3451"></a>Błąd kompilatora C3451

"attribute": nie można zastosować niezarządzanego atrybutu "type"

Atrybut C++ nie można zastosować do typu CLR. Zobacz [dokumentacja atrybutów C++](../../windows/attributes/attributes-alphabetical-reference.md) Aby uzyskać więcej informacji.

Aby uzyskać więcej informacji, zobacz [atrybuty zdefiniowane przez użytkownika](../../extensions/user-defined-attributes-cpp-component-extensions.md).

Ten błąd można wygenerować w wyniku pracy zgodności kompilatora, która została wykonana dla programu Visual C++ 2005: [uuid](../../windows/uuid-cpp-attributes.md) atrybut nie jest dozwolony dla atrybutu użytkownika przy użyciu CLR — programowanie. Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.GuidAttribute>.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3451.

```
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