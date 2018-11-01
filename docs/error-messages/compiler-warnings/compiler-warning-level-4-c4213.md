---
title: Kompilator ostrzeżenie (poziom 4) C4213
ms.date: 11/04/2016
f1_keywords:
- C4213
helpviewer_keywords:
- C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
ms.openlocfilehash: 8a3697b3bf63ac2a7a1e4e4bd0bf3a626c6bd631
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566130"
---
# <a name="compiler-warning-level-4-c4213"></a>Kompilator ostrzeżenie (poziom 4) C4213

użyto niestandardowego rozszerzenia: rzutowanie na wartościowanie lewostronne

Za pomocą domyślnego rozszerzenia Microsoft (/Ze) można użyć rzutowania, po lewej stronie instrukcji przypisania.

## <a name="example"></a>Przykład

```
// C4213.c
// compile with: /W4
void *a;
void f()
{
   int   i[3];
   a = &i;
   *(( int * )a )++ = 3;  // C4213
}

int main()
{
}
```

Takie rzutowania są nieprawidłowe w obszarze zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).