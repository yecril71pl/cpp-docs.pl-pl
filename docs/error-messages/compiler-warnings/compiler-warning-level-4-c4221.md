---
title: Kompilator ostrzeżenie (poziom 4) C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: f552a5d76d1a778cdf72cbe079138f609350ffb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511244"
---
# <a name="compiler-warning-level-4-c4221"></a>Kompilator ostrzeżenie (poziom 4) C4221

użyto niestandardowego rozszerzenia: 'Identyfikator': nie można zainicjować przy użyciu adresu automatycznej zmiennej

Za pomocą domyślnego rozszerzenia Microsoft (/Ze), można inicjować odpowiedni typ agregacji (**tablicy**, `struct`, lub **Unii**) przy użyciu adresu zmiennej lokalnej (automatyczne).

## <a name="example"></a>Przykład

```
// C4221.c
// compile with: /W4
struct S
{
   int *i;
};

void func()
{
   int j;
   struct S s1 = { &j };   // C4221
}

int main()
{
}
```

Takie inicjalizacje są nieprawidłowe w obszarze zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).