---
title: Kompilator ostrzeżenie (poziom 1) C4715 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4715
dev_langs:
- C++
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b3de829992bfa650280768a2fcd761feaeaece0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061373"
---
# <a name="compiler-warning-level-1-c4715"></a>Kompilator ostrzeżenie (poziom 1) C4715

'Funkcja': niewszystkie ścieżki kodu zwracają wartość

Określona funkcja potencjalnie nie może zwracać wartość.

## <a name="example"></a>Przykład

```
// C4715a.cpp
// compile with: /W1 /LD
int func1( int i )
{
   if( i )
   return 3;  // C4715 warning, nothing returned if i == 0
}
```

Aby uniknąć tego ostrzeżenia, należy zmodyfikować kod, tak aby wszystkie ścieżki przypisać wartość zwracaną do funkcji:

```
// C4715b.cpp
// compile with: /LD
int func1( int i )
{
   if( i ) return 3;
   else return 0;     // OK, always returns a value
}
```

Istnieje możliwość, że Twój kod może zawierać wywołania do funkcji, która nigdy nie wraca, jak w poniższym przykładzie:

```
// C4715c.cpp
// compile with: /W1 /LD
void fatal()
{
}
int glue()
{
   if(0)
      return 1;
   else if(0)
      return 0;
   else
      fatal();   // C4715
}
```

Ten kod generuje również ostrzeżenie, ponieważ kompilator nie może określić, że `fatal` nigdy nie zwraca. Aby zapobiec sytuacji, w której ten kod generuje komunikat o błędzie, Zadeklaruj `fatal` przy użyciu [__declspec(noreturn)](../../cpp/noreturn.md).