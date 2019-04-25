---
title: Kompilator ostrzeżenie (poziom 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 3a56e58d9bec1034a55f4e588dbddd0dba03f348
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208030"
---
# <a name="compiler-warning-level-1-c4076"></a>Kompilator ostrzeżenie (poziom 1) C4076

> "*modyfikatora typu*": nie można używać z typem "*typename*"

## <a name="remarks"></a>Uwagi

Modyfikator typu, czy jest to **podpisany** lub **niepodpisane**, nie można używać z typem danych nie jest liczbą całkowitą. *Modyfikator typu* jest ignorowana.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4076; Aby rozwiązać ten problem, Usuń **niepodpisane** modyfikatora typu:

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```