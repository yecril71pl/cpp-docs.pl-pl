---
title: Kompilator ostrzeżenie (poziom 1) C4010
ms.date: 11/04/2016
f1_keywords:
- C4010
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
ms.openlocfilehash: 40c6724daf17c1c0b546bb7bc64bb704f732e8d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441252"
---
# <a name="compiler-warning-level-1-c4010"></a>Kompilator ostrzeżenie (poziom 1) C4010

komentarz jednowierszowy zawiera znak kontynuacji wiersza

Komentarz jednowierszowy, który został wprowadzony przez / / zawiera ukośnik odwrotny (\\) który służy jako znak kontynuacji wiersza. Kompilator traktuje następny wiersz jako kontynuację i traktuje je jako komentarz.

Niektóre składni skierowane edytory nie wskazują wiersza po znaku kontynuacji jako komentarz. Ignoruj kolorowania na wszystkie wiersze, które powodują to ostrzeżenie.

Poniższy przykład spowoduje wygenerowanie C4010:

```
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```