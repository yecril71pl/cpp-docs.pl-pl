---
title: C3062 błąd kompilatora
ms.date: 11/04/2016
f1_keywords:
- C3062
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
ms.openlocfilehash: 6f4157db4a2a1b1864446a082deddc73df2e2fe9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406798"
---
# <a name="compiler-error-c3062"></a>C3062 błąd kompilatora

"enum": moduł wyliczający wymaga wartości, ponieważ podstawowy typ to "type"

Można określić typu podstawowego dla wyliczenia. Jednak niektóre typy wymagają przypisania wartości do każdego modułu wyliczającego.

Aby uzyskać więcej informacji na temat typów wyliczeniowych, zobacz [klasa wyliczeniowa](../../extensions/enum-class-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C3062:

```
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```