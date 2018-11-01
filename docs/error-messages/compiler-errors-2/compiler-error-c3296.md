---
title: Błąd kompilatora C3296
ms.date: 11/04/2016
f1_keywords:
- C3296
helpviewer_keywords:
- C3296
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
ms.openlocfilehash: 2e9787b063a5a37af8d0e0fdd04492a743792646
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588113"
---
# <a name="compiler-error-c3296"></a>Błąd kompilatora C3296

"właściwość": właściwość o tej nazwie już istnieje.

Kompilator napotkał więcej niż jedną właściwość o tej samej nazwie. Każdej właściwości w typie musi mieć unikatową nazwę.

Aby uzyskać więcej informacji, zobacz [właściwość](../../windows/property-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3296.

```
// C3296.cpp
// compile with: /clr /c
using namespace System;

ref class R {
public:
   property int MyProp[int] { int get(int); }

   property String^ MyProp[int] { void set(int, String^); }   // C3296
};
```