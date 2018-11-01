---
title: Kompilator ostrzeżenie (poziom 4) C4670
ms.date: 11/04/2016
f1_keywords:
- C4670
helpviewer_keywords:
- C4670
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
ms.openlocfilehash: 1ce32ef4d07ea5e2c6f328578837f805eed5c897
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633480"
---
# <a name="compiler-warning-level-4-c4670"></a>Kompilator ostrzeżenie (poziom 4) C4670

'Identyfikator': Ta klasa bazowa jest niedostępna

Określonej klasy bazowej obiektu, aby były generowane w **spróbuj** blok nie jest dostępny. Nie można utworzyć wystąpienia obiektu, jeśli zostanie on zgłoszony. Sprawdź, czy klasa bazowa jest dziedziczony ze specyfikatorem prawidłowy dostęp.

Poniższy przykład spowoduje wygenerowanie C4670:

```
// C4670.cpp
// compile with: /EHsc /W4
class A
{
};

class B : /* public */ A
{
} b;   // inherits A with private access by default

int main()
{
    try
    {
       throw b;   // C4670
    }
    catch( B )
    {
    }
}
```