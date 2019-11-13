---
title: Ostrzeżenie kompilatora (poziom 1) C4628
ms.date: 11/04/2016
f1_keywords:
- C4628
helpviewer_keywords:
- C4628
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
ms.openlocfilehash: 6063755db5ac517d868bc47d2c417356ccef5d58
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051440"
---
# <a name="compiler-warning-level-1-c4628"></a>Ostrzeżenie kompilatora (poziom 1) C4628

dwuznaki nieobsługiwane z -Ze. Sekwencja znaków 'dwuznak' nie jest interpretowana jako alternatywny token dla 'char'

Wykresy nie są obsługiwane w obszarze [/ze](../../build/reference/za-ze-disable-language-extensions.md). Po tym ostrzeżeniu zostanie zwrócony błąd.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Poniższy przykład generuje C4628:

```cpp
// C4628.cpp
// compile with: /WX
#pragma warning(default : 4628)
int main()
<%   // C4628 <% digraph for {
}
```