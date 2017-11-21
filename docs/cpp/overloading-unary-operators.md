---
title: "Przeładowanie operatorów Jednoargumentowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- unary operators [C++], plus
- increment operators [C++], overloaded
- unary operators [C++], minus
- operators [C++], unary
- redefinable unary operators [C++]
- unary operators [C++]
- pointer dereference operator overloading
- plus operator
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 54c3e7eff420c5ed562e71235d204800eff5019a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="overloading-unary-operators"></a>Przeładowanie operatorów jednoargumentowych
Operatory jednoargumentowe, które mogą być przeciążone, są następujące:  
  
1.  `!`([NEGACJA](../cpp/logical-negation-operator-exclpt.md))  
  
2.  `&`([adresu](../cpp/address-of-operator-amp.md))  
  
3.  `~`([osoby dopełnienia](../cpp/one-s-complement-operator-tilde.md))  
  
4.  `*`([wyłuskania wskaźnika](../cpp/indirection-operator-star.md))  
  
5.  `+`([jednoargumentowe plus](../cpp/additive-operators-plus-and.md))  
  
6.  `-`([negacji jednoargumentowy](../cpp/additive-operators-plus-and.md))  
  
7.  `++`([przyrostu](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))  
  
8.  `--`([dekrementacji](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))  
  
9. operatory konwersji  
  
 Operatory przyrostka inkrementacji i dekrementacji operatory (`++` i  **--** ) są traktowane odrębnie w [zwiększyć i zmniejszyć](../cpp/increment-and-decrement-operator-overloading-cpp.md).  
  
 Operatory konwersji omówiono także w innym temacie; zobacz [zdefiniowane przez użytkownika konwersje typów](../cpp/user-defined-type-conversions-cpp.md).  
  
 Następujące reguły są prawdziwe dla wszystkich innych operatorów jednoargumentowych. Aby zadeklarować funkcję operatora jednoargumentowego jako niestatyczny element członkowski, należy zadeklarować ją w postaci:  
  
 `ret-type operator` `op` `()`  
  
 gdzie `ret-type` jest zwracany typ i `op` jest jednym z podmiotów wymienione w powyższej tabeli.  
  
 Aby zadeklarować funkcję operatora jednoargumentowego jako funkcję globalną, należy zadeklarować ją w postaci:  
  
 `ret-type operator` `op` (`arg` )  
  
 gdzie `ret-type` i `op` są zgodnie z opisem dla funkcji Członkowskich operatora i `arg` jest argumentem typu klasy, w którym ma działać.  
  
> [!NOTE]
>  Nie ma żadnych ograniczeń pod względem typów zwracanych operatorów jednoargumentowych. Na przykład, warto dla NEGACJA (`!`) do zwrócenia z wartością całkowitą, ale nie jest wymuszana.  
  
## <a name="see-also"></a>Zobacz też  
 [Przeładowanie operatora](../cpp/operator-overloading.md)