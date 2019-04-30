---
title: Kompilator ostrzeżenie (poziom 1) C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: e32509e4d32eef4f53b8d43a7db769844f1182c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397240"
---
# <a name="compiler-warning-level-1-c4572"></a>Kompilator ostrzeżenie (poziom 1) C4572

Atrybut [ParamArray] jest przestarzały z opcją/CLR, użyj "..." Zamiast tego

Użyto przestarzały styl do określania listy zmiennych argumentów. Podczas kompilowania dla środowiska CLR, należy użyć składni wielokropka zamiast <xref:System.ParamArrayAttribute>. Aby uzyskać więcej informacji, zobacz [zmiennej listy argumentów (...) (C++Sposób niezamierzony) ](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4572.

```
// C4572.cpp
// compile with: /clr /W1
void Func([System::ParamArray] array<int> ^);   // C4572
void Func2(... array<int> ^){}   // OK

int main() {
   Func2(1, 2, 3);
}
```