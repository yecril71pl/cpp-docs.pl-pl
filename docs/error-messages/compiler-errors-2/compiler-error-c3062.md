---
title: C3062 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3062
dev_langs:
- C++
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95f2e58cada0b1b825fb0f065b461db6350de9fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067171"
---
# <a name="compiler-error-c3062"></a>C3062 błąd kompilatora

"enum": moduł wyliczający wymaga wartości, ponieważ podstawowy typ to "type"

Można określić typu podstawowego dla wyliczenia. Jednak niektóre typy wymagają przypisania wartości do każdego modułu wyliczającego.

Aby uzyskać więcej informacji na temat typów wyliczeniowych, zobacz [klasa wyliczeniowa](../../windows/enum-class-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C3062:

```
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```