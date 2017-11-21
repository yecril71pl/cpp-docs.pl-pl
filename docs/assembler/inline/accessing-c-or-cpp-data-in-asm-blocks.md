---
title: "Uzyskiwanie dostępu do danych C lub C++ w blokach __asm | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f9a7316c8db4e9f6d74b3cd762e24272caaf2f34
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="accessing-c-or-c-data-in-asm-blocks"></a>Uzyskiwanie dostępu do danych C lub C++ w blokach __asm
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Dużą wygodę wbudowany zestaw jest możliwość odwołuje się do zmiennej języka C lub C++ według nazwy. `__asm` Bloku może odwoływać się do żadnych symboli, w tym nazwy zmiennych, które znajdują się w zakresie, w którym pojawi się blok. Na przykład jeśli zmienna C `var` znajduje się w zakresie, instrukcja  
  
```  
__asm mov eax, var  
```  
  
 przechowuje wartość `var` w EAX.  
  
 Jeśli klasy, struktury lub elementu członkowskiego typu union ma unikatową nazwę, `__asm` bloku może odwoływać się do niego przy użyciu tylko nazwę elementu członkowskiego, bez określania zmiennej lub `typedef` nazwa przed okresem (**.**) operatora. Jeśli nazwa elementu członkowskiego nie jest unikatowa, jednak należy umieścić zmiennej lub `typedef` nazwa bezpośrednio przed operatorem okresu. Na przykład typy struktur w następującego udziału próbki `same_name` jak nazwa ich elementu członkowskiego:.  
  
 Deklarowanie zmiennych z typami  
  
```  
struct first_type hal;  
struct second_type oat;  
```  
  
 wszystkie odwołania do elementu członkowskiego `same_name` muszą używać nazwy zmiennej, ponieważ `same_name` nie jest unikatowa. Element członkowski, ale `weasel` ma unikatową nazwę, więc można odwołać się do niego przy użyciu nazwy elementu członkowskiego:  
  
```  
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
  
 Należy pamiętać, że nazwa zmiennej pominięcie jedynie udogodnienie kodowania. Z takimi samymi instrukcjami zestawu są generowane, czy nazwa zmiennej jest obecny.  
  
 Można uzyskać dostępu do elementów członkowskich danych w języku C++ bez względu na ograniczenia dostępu. Jednak nie można wywołać elementu członkowskiego funkcji.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Przy użyciu języka C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)