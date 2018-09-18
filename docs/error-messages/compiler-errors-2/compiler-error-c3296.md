---
title: Błąd kompilatora C3296 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3296
dev_langs:
- C++
helpviewer_keywords:
- C3296
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 585d9eaaf37b913a0be339ccabd230aa79142526
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016588"
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