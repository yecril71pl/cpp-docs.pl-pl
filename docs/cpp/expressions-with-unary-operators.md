---
title: "Wyrażenia z operatorami Jednoargumentowymi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 48ebd210b67f07847ceccec05625fe01eb15055b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="expressions-with-unary-operators"></a>Wyrażenia z operatorami jednoargumentowymi
Operatory jednoargumentowe działa tylko jedno operandu w wyrażeniu. Operatory jednoargumentowe są następujące:  
  
-   [Operator pośredni (*)](../cpp/indirection-operator-star.md)  
  
-   [Operator adresu (&)](../cpp/address-of-operator-amp.md)  
  
-   [Jednoargumentowe plus (+) — operator](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [Jednoargumentowy operator negacji (-)](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [Operator logiczny negacji (!)](../cpp/logical-negation-operator-exclpt.md)  
  
-   [Na jeden operator dopełnienia jednostkowego (~)](../cpp/one-s-complement-operator-tilde.md)  
  
-   [Prefiks operator inkrementacji (++)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [Operator dekrementacji prefiksu (-)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [Rzutowanie (operator)](../cpp/cast-operator-parens.md)  
  
-   [sizeof — operator](../cpp/sizeof-operator.md)  
  
-   [__uuidof operator](../cpp/uuidof-operator.md)  
  
-   [__alignof operator](../cpp/alignof-operator.md)  
  
-   [New — operator](../cpp/new-operator-cpp.md)  
  
-   [delete — operator](../cpp/delete-operator-cpp.md)  
  
 Operatorzy te mają łączność od prawej do lewej. Wyrażenie jednoargumentowe zazwyczaj obejmują składni poprzedzający przyrostek lub wyrażenia podstawowego.  
  
 Poniżej przedstawiono możliwe formy jednoargumentowy wyrażeń.  
  
-   *Operatory przyrostka wyrażenia*  
  
-   `++`*wyrażenie jednoargumentowe*  
  
-   `--`*wyrażenie jednoargumentowe*  
  
-   *operator jednoargumentowy* *wyrażenie cast*  
  
-   `sizeof`*wyrażenie jednoargumentowe*  
  
-   `sizeof(`*nazwy typu*`)`  
  
-   `decltype(`*wyrażenie*`)`  
  
-   *wyrażenie alokacji*  
  
-   *wyrażenie dezalokacji*  
  
 Wszelkie *wyrażenie przyrostek* jest uznawany za *wyrażenie jednoargumentowe*, i ponieważ przyjęto, że wszystkie wyrażenia podstawowego *przyrostek wyrażenie*, jest wszystkie wyrażenia podstawowe uznawane za *wyrażenie jednoargumentowe* również. Aby uzyskać więcej informacji, zobacz [wyrażenia przyrostków](../cpp/postfix-expressions.md) i [wyrażenia podstawowe](../cpp/primary-expressions.md).  
  
 A *operatora jednoargumentowego* składa się z co najmniej jeden z następujących symboli:`* & + - ! ~`  
  
 *Wyrażenie cast* wyrażenie jednoargumentowe z opcjonalne Rzutowanie na typ zmiany. Aby uzyskać więcej informacji, zobacz [Operator rzutowania: ()](../cpp/cast-operator-parens.md).  
  
 *Wyrażenie* może być dowolne wyrażenie. Aby uzyskać więcej informacji, zobacz [wyrażenia](../cpp/expressions-cpp.md).  
  
 *Wyrażenie alokacji* odwołuje się do `new` operatora. *Wyrażenie dezalokacji* odwołuje się do `delete` operatora. Aby uzyskać więcej informacji zobacz linki wcześniej w tym temacie.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy wyrażeń](../cpp/types-of-expressions.md)