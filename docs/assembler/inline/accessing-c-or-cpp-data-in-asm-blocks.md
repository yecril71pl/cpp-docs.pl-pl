---
title: Uzyskiwanie dostępu do danych C lub C++ w blokach __asm
ms.date: 08/30/2018
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
ms.openlocfilehash: 8fbe855c2f5de96d81e6c8a27c4bfcee0864f12c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193045"
---
# <a name="accessing-c-or-c-data-in-__asm-blocks"></a>Uzyskiwanie dostępu do danych C lub C++ w blokach __asm

**Specyficzne dla firmy Microsoft**

Doskonałym zestawem wbudowanym jest możliwość odwoływania się do zmiennych C lub C++ według nazwy. **`__asm`** Blok może odwoływać się do dowolnych symboli, w tym nazw zmiennych, które znajdują się w zakresie, w którym znajduje się blok. Na przykład jeśli zmienna C `var` znajduje się w zakresie, instrukcja

```cpp
__asm mov eax, var
```

przechowuje wartość `var` w EAX.

Jeśli klasa, struktura lub członek Unii ma unikatową nazwę, **`__asm`** blok może odwoływać się do niego tylko przy użyciu nazwy elementu członkowskiego bez określania zmiennej lub **`typedef`** nazwy przed operatorem kropki (**.**). Jeśli nazwa elementu członkowskiego nie jest unikatowa, należy jednak umieścić zmienną lub **`typedef`** nazwę bezpośrednio przed operatorem kropki. Na przykład typy struktury w następującym przykładowym udziale `same_name` jako nazwa elementu członkowskiego:.

Jeśli deklarujesz zmienne z typami

```cpp
struct first_type hal;
struct second_type oat;
```

wszystkie odwołania do elementu członkowskiego `same_name` muszą używać nazwy zmiennej, ponieważ `same_name` nie są unikatowe. Ale element członkowski `weasel` ma unikatową nazwę, więc można się do niego odwoływać tylko przy użyciu nazwy elementu członkowskiego:

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

Należy zauważyć, że pominięcie nazwy zmiennej jest tylko wygodą kodowania. Te same instrukcje dotyczące zestawu są generowane niezależnie od tego, czy nazwa zmiennej jest obecna.

Dostęp do danych można uzyskać w języku C++ bez względu na ograniczenia dostępu. Nie można jednak wywołać funkcji Członkowskich.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Używanie C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
