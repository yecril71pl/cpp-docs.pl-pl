---
title: Kompilator ostrzeżenie (poziom 4) C4706
ms.date: 11/04/2016
f1_keywords:
- C4706
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
ms.openlocfilehash: e57470fcd8e7b014084b094c9ca5e39f0a86d85e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630045"
---
# <a name="compiler-warning-level-4-c4706"></a>Kompilator ostrzeżenie (poziom 4) C4706

Przypisanie wewnątrz wyrażenia warunkowego

Wartość testu w wyrażeniu warunkowym był wynik przypisania.

Przypisania ma wartość (wartość po lewej stronie przypisania), który może służyć prawnie w innego wyrażenia, w tym wyrażeniu testowym.

Poniższy przykład spowoduje wygenerowanie C4706:

```
// C4706a.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a  = b ) // C4706
   {
   }
}
```

To ostrzeżenie wystąpi nawet wtedy, gdy dwukrotnie nawiasów wokół warunek testu:

```
// C4706b.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a  =  b ) ) // C4706
   {
   }
}
```

Jeśli masz zamiar do testowania relacji i przypisywanie, aby nie używać `==` operatora. Na przykład poniższy wiersz testów czy i b są takie same:

```
// C4706c.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a == b )
   {
   }
}
```

Jeśli zamierzasz utworzyć test wartość wynik przypisania test, aby upewnić się, że przydział jest różna od zera lub nie ma wartości null. Na przykład poniższy kod nie generuje to ostrzeżenie:

```
// C4706d.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a = b ) != 0 )
   {
   }
}
```