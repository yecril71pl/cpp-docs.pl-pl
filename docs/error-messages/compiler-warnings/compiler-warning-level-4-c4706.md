---
title: Kompilator ostrzeżenie (poziom 4) C4706 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4706
dev_langs:
- C++
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 843edeaf490f27475003e9303f7929b818e2b104
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036959"
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