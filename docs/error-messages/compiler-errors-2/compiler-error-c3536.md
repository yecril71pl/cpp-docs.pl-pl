---
title: Błąd kompilatora C3536
ms.date: 11/04/2016
f1_keywords:
- C3536
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
ms.openlocfilehash: 2380a9d42525cfb662fa014b89751d6dc8b9f192
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508254"
---
# <a name="compiler-error-c3536"></a>Błąd kompilatora C3536

"symbol": nie można użyć, zanim zostanie zainicjowany

Nie można użyć wskazanego symbolu przed jego zainicjowaniem. W tym przypadku oznacza to, że zmienna nie może zostać użyta do zainicjowania siebie.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Nie Inicjuj inicjacji zmiennej.

## <a name="example"></a>Przykład

Poniższy przykład daje C3536, ponieważ każda zmienna jest inicjowana z samym sobą.

```cpp
// C3536.cpp
// Compile with /Zc:auto
int main()
{
   auto a = a;     //C3536
   auto b = &b;    //C3536
   auto c = c + 1; //C3536
   auto* d = &d;   //C3536
   auto& e = e;    //C3536
   return 0;
};
```

## <a name="see-also"></a>Zobacz też

[Słowo kluczowe "Autouzupełnianie"](../../cpp/auto-cpp.md)
