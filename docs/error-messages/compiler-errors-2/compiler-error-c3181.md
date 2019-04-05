---
title: Błąd kompilatora C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: dc848d4108ed4a1a7b6646647a1bbb1ec8dcadf7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781812"
---
# <a name="compiler-error-c3181"></a>Błąd kompilatora C3181

"type": nieprawidłowy operand dla operatora

Nieprawidłowy parametr został przekazany do [typeid](../../extensions/typeid-cpp-component-extensions.md) operatora. Parametr musi być typu zarządzanego.

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
