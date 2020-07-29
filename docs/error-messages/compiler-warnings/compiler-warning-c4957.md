---
title: Ostrzeżenie kompilatora C4957
ms.date: 11/04/2016
f1_keywords:
- C4957
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
ms.openlocfilehash: ada10b5989b714ec4c75a24de1bbb101e1f51ee6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230769"
---
# <a name="compiler-warning-c4957"></a>Ostrzeżenie kompilatora C4957

> "*Cast*": jawne rzutowanie z "*cast_from*" na "*cast_to*" nie jest możliwe do zweryfikowania

## <a name="remarks"></a>Uwagi

Rzutowanie spowoduje niemożliwy do sprawdzenia obraz.

Niektóre rzuty są bezpieczne (na przykład, **`static_cast`** która wyzwala konwersje zdefiniowane przez użytkownika i **`const_cast`** ). [Safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) jest gwarantowany do tworzenia kodu możliwego do zweryfikowania.

Aby uzyskać więcej informacji, zobacz [czysty i możliwy do zweryfikowania kod (C++/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Opcja " **/CLR: Safe** Compiler" jest przestarzała w programie visual Studio 2015 i nie jest obsługiwana w programie visual Studio 2017.

To ostrzeżenie jest wydawane jako błąd i można je wyłączyć za pomocą dyrektywy pragma [Warning](../../preprocessor/warning.md) lub opcji kompilatora [/WD](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C4957:

```cpp
// C4957.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4957 )
using namespace System;
int main() {
   Object ^ o = "Hello, World!";
   String ^ s = static_cast<String^>(o);   // C4957
   String ^ s2 = safe_cast<String^>(o);   // OK
}
```
