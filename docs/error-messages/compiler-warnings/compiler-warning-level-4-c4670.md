---
title: Kompilator ostrzeżenie (poziom 4) C4670 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4670
dev_langs:
- C++
helpviewer_keywords:
- C4670
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f1f406442e763175da1bb0220925a1a43d8825d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118261"
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