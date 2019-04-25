---
title: Ostrzeżenie kompilatora C4950
ms.date: 11/04/2016
f1_keywords:
- C4950
helpviewer_keywords:
- C4950
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
ms.openlocfilehash: 784179af68ff55ba70c61255c88688105ecb1738
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208099"
---
# <a name="compiler-warning-c4950"></a>Ostrzeżenie kompilatora C4950

"type_or_member": oznaczony jako przestarzały

Element członkowski lub typ został oznaczony jako przestarzały z <xref:System.ObsoleteAttribute> atrybutu.

C4950 zawsze jest wystawiany jako błąd. Możesz wyłączyć to ostrzeżenie używając [ostrzeżenie](../../preprocessor/warning.md) dyrektywa pragmy lub [/wd](../../build/reference/compiler-option-warning-level.md) — opcja kompilatora.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4950:

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