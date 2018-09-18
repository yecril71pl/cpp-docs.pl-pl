---
title: Kompilator ostrzeżenie (poziom 3) C4390 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4390
dev_langs:
- C++
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83131119e360bcf8193c2d6c8ca5a3cd09341516
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054197"
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