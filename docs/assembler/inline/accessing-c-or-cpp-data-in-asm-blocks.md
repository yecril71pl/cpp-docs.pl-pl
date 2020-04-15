---
title: Uzyskiwanie dostępu do danych C lub C++ w blokach __asm
ms.date: 08/30/2018
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
ms.openlocfilehash: b4341f87226118906749dcdb18b9227e68be6a23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318091"
---
# <a name="accessing-c-or-c-data-in-__asm-blocks"></a>Uzyskiwanie dostępu do danych C lub C++ w blokach __asm

**Specyficzne dla firmy Microsoft**

Dużą wygodą zestawu wbudowanego jest możliwość odwoływania się do zmiennych C lub C++ według nazwy. Blok `__asm` może odwoływać się do dowolnych symboli, w tym nazw zmiennych, które znajdują się w zakresie, w którym pojawia się blok. Na przykład, jeśli `var` zmienna C jest w zakresie, instrukcja

```cpp
__asm mov eax, var
```

przechowuje wartość `var` w EAX.

Jeśli klasa, struktura lub element członkowski unii `__asm` ma unikatową nazwę, blok może odwoływać się `typedef` do niego przy użyciu tylko nazwy elementu członkowskiego, bez określania zmiennej lub nazwy przed operatorem kropki (**.**). Jeśli jednak nazwa elementu członkowskiego nie jest unikatowa, należy umieścić zmienną lub `typedef` nazwę bezpośrednio przed operatorem okresu. Na przykład typy struktury w `same_name` poniższym przykładowym udziale jako ich nazwa elementu członkowskiego:.

W przypadku deklarowania zmiennych z typami

```cpp
struct first_type hal;
struct second_type oat;
```

wszystkie odwołania do `same_name` elementu członkowskiego musi `same_name` używać nazwy zmiennej, ponieważ nie jest unikatowy. Ale element `weasel` członkowski ma unikatową nazwę, więc można odwoływać się do niego przy użyciu tylko jego nazwę członka:

```cpp
// InlineAssembler_Accessing_C_asm_Blocks.cpp
// processor: x86
#include <stdio.h>
struct first_type
{
   char *weasel;
   int same_name;
};

struct second_type
{
   int wonton;
   long same_name;
};

int main()
{
   struct first_type hal;
   struct second_type oat;

   __asm
   {
      lea ebx, hal
      mov ecx, [ebx]hal.same_name ; Must use 'hal'
      mov esi, [ebx].weasel       ; Can omit 'hal'
   }
   return 0;
}
```

Należy zauważyć, że pominięcie nazwy zmiennej jest jedynie wygodą kodowania. Te same instrukcje zestawu są generowane niezależnie od tego, czy nazwa zmiennej jest obecna.

Można uzyskać dostęp do elementów członkowskich danych w języku C++ bez względu na ograniczenia dostępu. Jednak nie można wywołać funkcji członkowskich.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[Korzystanie z C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
