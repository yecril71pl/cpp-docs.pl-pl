---
title: Kompilator ostrzeżenie (poziom 2) C4309
ms.date: 11/04/2016
f1_keywords:
- C4309
helpviewer_keywords:
- C4309
ms.assetid: cb3f41ef-fd8a-4def-baa1-924e751fca68
ms.openlocfilehash: 41184571dc07213c796c039170966a0c7150bd45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402479"
---
# <a name="compiler-warning-level-2-c4309"></a>Kompilator ostrzeżenie (poziom 2) C4309

'conversion': obcięcie stałej wartości

Konwersja typu powoduje, że stała przekracza ilość miejsca przydzielonego dla niego. Użytkownik może być konieczne użycie większych typ stałej.

Poniższy przykład spowoduje wygenerowanie C4309:

```
// C4309.cpp
// compile with: /W2
int main()
{
   char c = 128;   // C4309
}
```