---
title: Kompilator ostrzeżenie (poziom 4) C4125 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4125
dev_langs:
- C++
helpviewer_keywords:
- C4125
ms.assetid: a081d1f4-0789-4915-91df-7ff0b28ca245
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7042dd8689bf5a9bafc35d6bdaa6028f0c52df2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087243"
---
# <a name="compiler-warning-level-4-c4125"></a>Kompilator ostrzeżenie (poziom 4) C4125

cyfra dziesiętna kończy ósemkową sekwencja ucieczki

Kompilator ocenia ósemkowej bez cyfry dziesiętne i przyjęto założenie, że cyfrę dziesiętną, jest znakiem.

## <a name="example"></a>Przykład

```
// C4125a.cpp
// compile with: /W4
char array1[] = "\709"; // C4125
int main()
{
}
```

Jeśli cyfry 9 jest przeznaczony jako znak, popraw następujący przykład:

```
// C4125b.cpp
// compile with: /W4
char array[] = "\0709";  // C4125 String containing "89"
int main()
{
}
```