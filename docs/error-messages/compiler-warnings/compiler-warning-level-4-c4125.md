---
title: Kompilator ostrzeżenie (poziom 4) C4125
ms.date: 11/04/2016
f1_keywords:
- C4125
helpviewer_keywords:
- C4125
ms.assetid: a081d1f4-0789-4915-91df-7ff0b28ca245
ms.openlocfilehash: 3b82bfd1a1acff07a0fd47bbd2abfb08178a74c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401361"
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