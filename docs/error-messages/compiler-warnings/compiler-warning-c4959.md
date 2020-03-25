---
title: Ostrzeżenie kompilatora C4959
ms.date: 11/04/2016
f1_keywords:
- C4959
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
ms.openlocfilehash: 13d2ed705bff7b42eb3c348692a5829bd54158b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164875"
---
# <a name="compiler-warning-c4959"></a>Ostrzeżenie kompilatora C4959

> nie można zdefiniować niezarządzanej struktury "*Type*" w/CLR: Safe, ponieważ dostęp do jej elementów członkowskich daje kod niemożliwy do zweryfikowania

## <a name="remarks"></a>Uwagi

Uzyskanie dostępu do elementu członkowskiego typu niezarządzanego spowoduje utworzenie obrazu (peverify. exe), który ma być możliwy do zweryfikowania.

Aby uzyskać więcej informacji, zobacz [czysty i możliwy doC++zweryfikowania kod (/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Opcja " **/CLR: Safe** Compiler" jest przestarzała w programie visual Studio 2015 i nie jest obsługiwana w programie visual Studio 2017.

To ostrzeżenie jest wydawane jako błąd i można je wyłączyć za pomocą dyrektywy pragma [Warning](../../preprocessor/warning.md) lub opcji kompilatora [/WD](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C4959:

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
