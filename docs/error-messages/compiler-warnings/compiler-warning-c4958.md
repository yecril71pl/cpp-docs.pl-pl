---
title: Ostrzeżenie kompilatora C4958
ms.date: 11/04/2016
f1_keywords:
- C4958
helpviewer_keywords:
- C4958
ms.assetid: e79b9e9c-d572-4a3a-a3b6-60962b70864a
ms.openlocfilehash: 7d4ac6f21cfcfe0f37eb17ff81eabd3e6341a7d5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477405"
---
# <a name="compiler-warning-c4958"></a>Ostrzeżenie kompilatora C4958

> "*operacji*": arytmetyka wskaźnika nie jest możliwe do zweryfikowania

## <a name="remarks"></a>Uwagi

Za pomocą arytmetyki wskaźnika dadzą nieweryfikowalnego obrazu.

Aby uzyskać więcej informacji, zobacz [czystej i możliwe do zweryfikowania kodu (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

**/CLR: Safe** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Ostrzeżenie to jest wydana jako błąd i mogą zostać wyłączone za pomocą [ostrzeżenie](../../preprocessor/warning.md) pragma lub [/wd](../../build/reference/compiler-option-warning-level.md) — opcja kompilatora.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4958:

```cpp
// C4958.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4958 )
using namespace System;

int main( ) {
   Int32 arr[] = new Int32[10];
   Int32* p = &arr[0];
   p++;   // C4958
}
```

Kompilator implementuje operacje arytmetyka wskaźnika tablicy. W związku z tym tablice natywnego nie są możliwe do zweryfikowania; Zamiast tego użyj tablicy CLR. Aby uzyskać więcej informacji, zobacz [tablicy](../../windows/arrays-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C4958:

```cpp
// C4958b.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4958 )

int main() {
   int array[5];
   array[4] = 0;   // C4958
}
```