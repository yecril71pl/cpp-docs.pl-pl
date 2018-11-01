---
title: Ostrzeżenie kompilatora C4959
ms.date: 11/04/2016
f1_keywords:
- C4959
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
ms.openlocfilehash: 646347dec7bc2bac7fa73c8f754d2f9549cb2ba6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473661"
---
# <a name="compiler-warning-c4959"></a>Ostrzeżenie kompilatora C4959

> Nie można zdefiniować niezarządzanego struct "*typu*" w/CLR: Safe, ponieważ dostęp do jego składowych daje nieweryfikowalny kod

## <a name="remarks"></a>Uwagi

Dostęp do składowej typu niezarządzanego dadzą obrazu nieweryfikowalnego (peverify.exe).

Aby uzyskać więcej informacji, zobacz [czystej i możliwe do zweryfikowania kodu (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

**/CLR: Safe** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Ostrzeżenie to jest wydana jako błąd i mogą zostać wyłączone za pomocą [ostrzeżenie](../../preprocessor/warning.md) pragma lub [/wd](../../build/reference/compiler-option-warning-level.md) — opcja kompilatora.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4959:

```cpp
// C4959.cpp
// compile with: /clr:safe

// Uncomment the following line to resolve.
// #pragma warning( disable : 4959 )
struct X {
   int data;
};

int main() {
   X x;
   x.data = 10;   // C4959
}
```