---
title: Błąd kompilatora C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: b37b28b4332b46aaaf803f58090a72c25e83f47f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587762"
---
# <a name="compiler-error-c3181"></a>Błąd kompilatora C3181

"type": nieprawidłowy operand dla operatora

Nieprawidłowy parametr został przekazany do [typeid](../../windows/typeid-cpp-component-extensions.md) operatora. Parametr musi być typu zarządzanego.

Należy pamiętać, że kompilator używa aliasów dla natywnych typów, które mapują do typów w środowisko uruchomieniowe języka wspólnego.

Poniższy przykład spowoduje wygenerowanie C3181:

```
// C3181a.cpp
// compile with: /clr
using namespace System;

int main() {
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181
   Type ^pType2 = int::typeid;   // OK
}
```
