---
title: Uzyskiwanie dostępu do danych C lub C++ w blokach __asm
ms.date: 08/30/2018
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
ms.openlocfilehash: 1f56cc5c049c1501ea09c76f31be3ab9dea5ed10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433062"
---
# <a name="accessing-c-or-c-data-in-asm-blocks"></a>Uzyskiwanie dostępu do danych C lub C++ w blokach __asm

**Microsoft Specific**

Doskonałe wygodę wbudowany zestaw jest możliwość odwoływania się do zmiennych C lub C++ według nazwy. `__asm` Bloku mogą odwoływać się do żadnych symboli, w tym nazwy zmiennych, które znajdują się w zakresie, gdzie pojawia się blok. Na przykład jeśli zmienna C `var` znajduje się w zakresie, instrukcja

```cpp
__asm mov eax, var
```

przechowuje wartość `var` w EAX.

Jeśli klasy, struktury lub Unii ma unikatową nazwę `__asm` bloku mogą odwoływać się do niej przy użyciu tylko nazwy elementu członkowskiego bez określenia zmiennej lub `typedef` nazwa przed kropką (**.**) — operator. Jeśli nazwa elementu członkowskiego nie jest unikatowa, jednak należy umieścić zmienną lub `typedef` nazwę tuż przed operatora kropki. Na przykład typy struktur w blokach następującego udziału przykładowe `same_name` jako swojej nazwy członka:.

Przy deklarowaniu zmiennych z typami

```cpp
struct first_type hal;
struct second_type oat;
```

wszystkie odwołania do elementu członkowskiego `same_name` należy użyć nazwy zmiennych, ponieważ `same_name` nie jest unikatowa. Element członkowski, ale `weasel` ma unikatową nazwę, dzięki czemu mogą odwoływać się do niego przy użyciu nazwy elementu członkowskiego:

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

Należy zauważyć, że nazwa zmiennej z pominięciem jedynie udogodnienie kodowania. Tych samych instrukcji zestawu są generowane, czy nazwa zmiennej jest obecny.

Można uzyskać dostęp do elementów członkowskich danych w języku C++ bez względu na ograniczenia dostępu. Jednak nie można wywołać element członkowski funkcji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>