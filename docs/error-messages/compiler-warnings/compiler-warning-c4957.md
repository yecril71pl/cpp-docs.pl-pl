---
title: C4957 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4957
dev_langs:
- C++
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60cf1c03ace94c866b77c5340e2a04a9d8190e4d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705221"
---
# <a name="compiler-warning-c4957"></a>C4957 ostrzeżenia kompilatora

> "*rzutowania*": jawne rzutowanie z "*cast_from*"do"*cast_to*" nie jest możliwe do zweryfikowania

## <a name="remarks"></a>Uwagi

Rzutowanie spowoduje niemożliwy obrazu.

Niektóre rzutowania są bezpieczne (na przykład `static_cast` która wyzwala konwersje zdefiniowane przez użytkownika i `const_cast`). A [safe_cast](../../windows/safe-cast-cpp-component-extensions.md) może utworzyć weryfikowalny kod.

Aby uzyskać więcej informacji, zobacz [czystej i weryfikowalny kod (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

**/CLR: Safe** — opcja kompilatora jest przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

To ostrzeżenie jest wystawione jako błąd i może być wyłączone z [ostrzeżenie](../../preprocessor/warning.md) pragma lub [/wd](../../build/reference/compiler-option-warning-level.md) — opcja kompilatora.

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