---
title: Kompilator ostrzeżenie (poziom 4) C4242
ms.date: 11/04/2016
f1_keywords:
- C4242
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
ms.openlocfilehash: e0582f3dfdd223b4571e361dc69fae1990aeea1c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401010"
---
# <a name="compiler-warning-level-4-c4242"></a>Kompilator ostrzeżenie (poziom 4) C4242

'Identyfikator': konwersja z 'Typ1' na 'Typ2', możliwa utrata danych

Typy są różne. Konwersja typu może spowodować utratę danych. Kompilator sprawia, że konwersja typu.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

Aby uzyskać dodatkowe informacje na temat C4242, zobacz [typowe błędy kompilatora](/windows/desktop/WinProg64/common-compiler-errors).

Poniższy przykład spowoduje wygenerowanie C4242:

```
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