---
title: Błąd kompilatora C3451 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3451
dev_langs:
- C++
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8685b75684827b4f202317e1df72a8248f1b41dc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085202"
---
# <a name="compiler-error-c3451"></a>Błąd kompilatora C3451

"attribute": nie można zastosować niezarządzanego atrybutu "type"

Atrybut C++ nie można zastosować do typu CLR. Zobacz [dokumentacja atrybutów C++](../../windows/cpp-attributes-reference.md) Aby uzyskać więcej informacji.

Aby uzyskać więcej informacji, zobacz [atrybuty zdefiniowane przez użytkownika](../../windows/user-defined-attributes-cpp-component-extensions.md).

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