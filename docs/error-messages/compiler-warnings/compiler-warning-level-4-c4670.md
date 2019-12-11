---
title: Ostrzeżenie kompilatora (poziom 4) C4670
ms.date: 11/04/2016
f1_keywords:
- C4670
helpviewer_keywords:
- C4670
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
ms.openlocfilehash: 3ea32e8693fbe310b82eeeb87b1e97f2281ddf04
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990751"
---
# <a name="compiler-warning-level-4-c4670"></a>Ostrzeżenie kompilatora (poziom 4) C4670

"Identyfikator": Ta klasa bazowa jest niedostępna

Określona klasa bazowa obiektu, który ma zostać zgłoszony w bloku **try** , jest niedostępna. Nie można utworzyć wystąpienia obiektu, jeśli został zgłoszony. Sprawdź, czy klasa bazowa jest dziedziczona z prawidłowym specyfikatorem dostępu.

Poniższy przykład generuje C4670:

```cpp
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
