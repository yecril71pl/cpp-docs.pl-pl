---
title: Ostrzeżenie kompilatora C4950
ms.date: 11/04/2016
f1_keywords:
- C4950
helpviewer_keywords:
- C4950
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
ms.openlocfilehash: 52c4de94dfe087b4dcf407295e556c9350b2cb8b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164992"
---
# <a name="compiler-warning-c4950"></a>Ostrzeżenie kompilatora C4950

"type_or_member": oznaczono jako przestarzały

Element członkowski lub typ został oznaczony jako przestarzały z atrybutem <xref:System.ObsoleteAttribute>.

C4950 jest zawsze wystawiony jako błąd. To ostrzeżenie można wyłączyć za pomocą dyrektywy pragma [Warning](../../preprocessor/warning.md) lub opcji kompilatora [/WD](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C4950:

```cpp
// C4950.cpp
// compile with: /clr
using namespace System;

// Any reference to Func3 should generate an error with message
[System::ObsoleteAttribute("Will be removed in next version", true)]
Int32 Func3(Int32 a, Int32 b) {
   return (a + b);
}

int main() {
   Int32 MyInt3 = ::Func3(2, 2);   // C4950
}
```
