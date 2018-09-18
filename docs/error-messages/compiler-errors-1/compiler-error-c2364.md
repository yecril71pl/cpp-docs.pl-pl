---
title: Błąd kompilatora C2364 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2364
dev_langs:
- C++
helpviewer_keywords:
- C2364
ms.assetid: 4f550571-94b5-42ca-84cb-663fecbead44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d35701eb47bdf633377652094b847ccdfb31e59
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100633"
---
# <a name="compiler-error-c2364"></a>Błąd kompilatora C2364

"type": niedozwolony typ niestandardowegp atrybutu

Argumenty nazwane dla atrybutów niestandardowych, które są ograniczone do stałych w czasie kompilacji. Na przykład typów całkowitych (int, char itp.), System::Type ^ i System::Object ^.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2364.

```
// c2364.cpp
// compile with: /clr /c
using namespace System;

[attribute(AttributeTargets::All)]
public ref struct ABC {
public:
   // Delete the following line to resolve.
   ABC( Enum^ ) {}   // C2364
   ABC( int ) {}   // OK
};
```