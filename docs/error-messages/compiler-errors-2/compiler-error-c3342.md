---
title: Błąd kompilatora C3342 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3342
dev_langs:
- C++
helpviewer_keywords:
- C3342
ms.assetid: 5c6d784f-bebe-4f7e-8615-44ca6f78bfba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03226ff4f7a5280827201a595b09a4779c88bb41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082108"
---
# <a name="compiler-error-c3342"></a>Błąd kompilatora C3342

"attribute": niejednoznaczny atrybut

Kompilator znaleziono więcej niż jedną definicję atrybutu.

Atrybut został zdefiniowany więcej niż jeden raz.

Aby uzyskać więcej informacji, zobacz [atrybuty zdefiniowane przez użytkownika](../../windows/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3342.

```
// C3342.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Reflection;

[AttributeUsage(AttributeTargets::All)]
public ref class XAttribute : public  Attribute {};

[AttributeUsage(AttributeTargets::All)]
public ref class X : public Attribute {};

[X]   // C3342 could refer to X or XAttribute
// try the following line instead
// [XAttribute]
public ref class Class4 {};
```