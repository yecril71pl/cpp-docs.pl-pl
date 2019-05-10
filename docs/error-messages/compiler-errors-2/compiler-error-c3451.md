---
title: Błąd kompilatora C3451
ms.date: 11/04/2016
f1_keywords:
- C3451
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
ms.openlocfilehash: 07cfda76af26ddb285be4f77131aaf48a20a761f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447857"
---
# <a name="compiler-error-c3451"></a>Błąd kompilatora C3451

"attribute": nie można zastosować niezarządzanego atrybutu "type"

Atrybut C++ nie można zastosować do typu CLR. Zobacz [dokumentacja atrybutów C++](../../windows/attributes/attributes-alphabetical-reference.md) Aby uzyskać więcej informacji.

Aby uzyskać więcej informacji, zobacz [atrybuty zdefiniowane przez użytkownika](../../extensions/user-defined-attributes-cpp-component-extensions.md).

Ten błąd można wygenerować w wyniku pracy zgodności kompilatora, która została wykonana dla programu Visual Studio 2005: [uuid](../../windows/uuid-cpp-attributes.md) atrybut nie jest dozwolony dla atrybutu użytkownika przy użyciu CLR — programowanie. Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.GuidAttribute>.

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