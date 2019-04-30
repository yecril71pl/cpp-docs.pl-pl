---
title: Ostrzeżenie kompilatora C4957
ms.date: 11/04/2016
f1_keywords:
- C4957
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
ms.openlocfilehash: 79a1b516db1508c755693b67ca2e4070095839da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388672"
---
# <a name="compiler-warning-c4957"></a>Ostrzeżenie kompilatora C4957

> "*rzutowania*": jawne rzutowanie z "*cast_from*"to"*cast_to*" nie jest możliwe do zweryfikowania

## <a name="remarks"></a>Uwagi

Rzutowania spowoduje nieweryfikowalnego obrazu.

Niektóre rzutowania są bezpieczne (na przykład `static_cast` , wyzwala konwersje zdefiniowane przez użytkownika i `const_cast`). A [safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) jest gwarantowane do tworzenia kodu możliwe do zweryfikowania.

Aby uzyskać więcej informacji, zobacz [czystej i weryfikowalny kod (C++sposób niezamierzony)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

**/CLR: Safe** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Ostrzeżenie to jest wydana jako błąd i mogą zostać wyłączone za pomocą [ostrzeżenie](../../preprocessor/warning.md) pragma lub [/wd](../../build/reference/compiler-option-warning-level.md) — opcja kompilatora.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4957:

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