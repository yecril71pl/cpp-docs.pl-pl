---
title: Ostrzeżenie kompilatora (poziom 4) C4127
ms.date: 10/16/2019
f1_keywords:
- C4127
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
ms.openlocfilehash: afca92602aa6033c56869d3f84192ca0f029a23e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218120"
---
# <a name="compiler-warning-level-4-c4127"></a>Ostrzeżenie kompilatora (poziom 4) C4127

> wyrażenie warunkowe jest stałą

## <a name="remarks"></a>Uwagi

Wyrażenie kontrolne **`if`** instrukcji lub pętli jest **`while`** obliczane jako stała. Ze względu na typowe użycie idiomatyczne, zaczynając od programu Visual Studio 2015 Update 3, proste stałe, takie jak 1 lub **`true`** nie wyzwalają ostrzeżenia, chyba że są wynikiem operacji w wyrażeniu.

Jeśli wyrażenie kontrolne **`while`** pętli jest stałą, ponieważ pętla opuszcza środek, rozważ zastąpienie pętli pętlą **`while`** **`for`** . Możesz pominąć inicjalizację, test zakończenia i przyrost pętli pętli **`for`** , co powoduje nieskończoność pętli, podobnie jak `while(1)` i można opuścić pętlę z treści **`for`** instrukcji.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia dwa sposoby C4127 jest generowany i pokazuje, jak używać pętli for, aby uniknąć ostrzeżenia:

```cpp
// C4127.cpp
// compile with: /W4
#include <stdio.h>
int main() {
   if (true) {}           // OK in VS2015 update 3 and later
   if (1 == 1) {}         // C4127
   while (42) { break; }  // C4127

   // OK
   for ( ; ; ) {
      printf("test\n");
      break;
   }
}
```

To ostrzeżenie można również wygenerować, gdy w wyrażeniu warunkowym jest używana stała czasu kompilacji:

```cpp
#include <string>

using namespace std;

template<size_t S, class T>
void MyFunc()
{
   if (sizeof(T) >= S) // C4127. "Consider using 'if constexpr' statement instead"
   {
   }
}

class Foo
{
   int i;
   string s;
};

int main()
{
   Foo f;
   MyFunc<4, Foo>();
}
```
