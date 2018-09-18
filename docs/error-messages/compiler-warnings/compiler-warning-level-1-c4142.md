---
title: Kompilator ostrzeżenie (poziom 1) C4142 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4142
dev_langs:
- C++
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 011f71c1d57f03c2be9bac3df67cd0ed90aa8017
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117390"
---
# <a name="compiler-warning-level-1-c4142"></a>Kompilator ostrzeżenie (poziom 1) C4142

nieszkodliwa ponowna definicja typu

Typ jest ponownie zdefiniować w taki sposób, który nie ma wpływu na wygenerowany kod.

Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny:

- Funkcji składowej klasy pochodnej ma inny typ zwracany z odpowiedniej funkcji składowej klasy bazowej.

- Typ zdefiniowany przy użyciu `typedef` polecenie zostało przedefiniowane przy użyciu różnej składni.

Poniższy przykład spowoduje wygenerowanie C4142:

```
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```