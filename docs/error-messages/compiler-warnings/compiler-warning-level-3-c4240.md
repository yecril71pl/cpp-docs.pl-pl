---
title: Kompilator ostrzeżenie (poziom 3) C4240
ms.date: 11/04/2016
f1_keywords:
- C4240
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
ms.openlocfilehash: fe5306cc7909138fea0159553b53c2adc6a46dc0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498244"
---
# <a name="compiler-warning-level-3-c4240"></a>Kompilator ostrzeżenie (poziom 3) C4240

użyto niestandardowego rozszerzenia: dostęp do "classname" teraz zdefiniowany jako "specyfikator dostępu", poprzednio został zdefiniowany jako "specyfikatorze dostępu"

W obszarze zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), nie można zmienić dostępu do klasy zagnieżdżonej. W obszarze domyślna rozszerzenia Microsoft (/Ze) można za pomocą tego ostrzeżenia.

## <a name="example"></a>Przykład

```
// C4240.cpp
// compile with: /W3
class X
{
private:
   class N;
public:
   class N
   {   // C4240
   };
};

int main()
{
}
```