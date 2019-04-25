---
title: Ostrzeżenie kompilatora C4956
ms.date: 11/04/2016
f1_keywords:
- C4956
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
ms.openlocfilehash: c15de8b22f56a2555cc763a45153139b1df01a31
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280845"
---
# <a name="compiler-warning-c4956"></a>Ostrzeżenie kompilatora C4956

> "*typu*": ten typ nie jest możliwe do zweryfikowania

## <a name="remarks"></a>Uwagi

To ostrzeżenie jest generowana podczas [/CLR: Safe](../../build/reference/clr-common-language-runtime-compilation.md) jest określony, a kod zawiera typ, który nie jest możliwe do zweryfikowania. **/CLR: Safe** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Aby uzyskać więcej informacji, zobacz [czystej i weryfikowalny kod (C++sposób niezamierzony)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Ostrzeżenie to jest wydana jako błąd i mogą zostać wyłączone za pomocą [ostrzeżenie](../../preprocessor/warning.md) pragma lub [/wd](../../build/reference/compiler-option-warning-level.md) — opcja kompilatora.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4956:

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```