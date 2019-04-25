---
title: Błąd kompilatora C3749
ms.date: 11/04/2016
f1_keywords:
- C3749
helpviewer_keywords:
- C3749
ms.assetid: 3d26b468-4757-41b8-b5a2-78022a5295fb
ms.openlocfilehash: 7535f82a392f3d54b265ada2bd40a8d433838f4b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227276"
---
# <a name="compiler-error-c3749"></a>Błąd kompilatora C3749

"attribute": atrybut niestandardowy nie można używać wewnątrz funkcji

Atrybut niestandardowy nie można używać wewnątrz funkcji. Aby uzyskać więcej informacji na temat atrybutów niestandardowych, zobacz temat [atrybutu](../../windows/attributes/attribute.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3749:

```
// C3749a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
public ref struct ABC : public Attribute {
   ABC() {}
};

void f1() { [ABC]; };  // C3749
```
