---
title: Ostrzeżenie kompilatora (poziom 4) C4242
ms.date: 11/04/2016
f1_keywords:
- C4242
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
ms.openlocfilehash: 3123a414dc7a169d2a472dad96d659a9e56c9020
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541748"
---
# <a name="compiler-warning-level-4-c4242"></a>Ostrzeżenie kompilatora (poziom 4) C4242

"Identyfikator": konwersja z "type1" na "type2", możliwa utrata danych

Typy są różne. Konwersja typu może spowodować utratę danych. Kompilator wykonuje konwersję typu.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Aby uzyskać dodatkowe informacje na temat C4242, zobacz [typowe błędy kompilatora](/windows/win32/WinProg64/common-compiler-errors).

Poniższy przykład generuje C4242:

```cpp
// C4242.cpp
// compile with: /W4
#pragma warning(4:4242)
int func() {
   return 0;
}

int main() {
   char a;
   a = func();   // C4242, return type and variable type do not match
}
```