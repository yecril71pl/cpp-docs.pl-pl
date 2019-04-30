---
title: Kompilator ostrzeżenie (poziom 3) C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 4ca00f892adc8fe3ac1bffb59a27ea1744249dea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401985"
---
# <a name="compiler-warning-level-3-c4390"></a>Kompilator ostrzeżenie (poziom 3) C4390

";": pusty kontrolowanego instrukcji znalezionej; to jest celem?

Po instrukcji sterowania, który nie zawiera instrukcji można odnaleźć średnikiem.

Jeśli otrzymasz C4390 ze względu na makra, należy użyć [ostrzeżenie](../../preprocessor/warning.md) pragma może wyłączyć C4390 w module zawierający makra.

Poniższy przykład spowoduje wygenerowanie C4390:

```
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```