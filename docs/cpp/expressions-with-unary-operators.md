---
title: Wyrażenia z operatorami Jednoargumentowymi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9301d4fdb09c63b7dc8e875e2b03a4990acec054
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941161"
---
# <a name="expressions-with-unary-operators"></a>Wyrażenia z operatorami jednoargumentowymi
Operatory jednoargumentowe działa tylko jeden argument w wyrażeniu. Operatory jednoargumentowe, są następujące:  
  
-   [Operator pośredni (*)](../cpp/indirection-operator-star.md)  
  
-   [Operator Address-of (&)](../cpp/address-of-operator-amp.md)  
  
-   [Jednoargumentowy operator (+) plus](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [Jednoargumentowy operator negacji (-)](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [Operator logiczny negacji (!)](../cpp/logical-negation-operator-exclpt.md)  
  
-   [Operator dopełnienia jednostkowego (~)](../cpp/one-s-complement-operator-tilde.md)  
  
-   [Prefiks operator inkrementacji (++)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [Prefiks operator dekrementacji (--)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [CAST — operator)](../cpp/cast-operator-parens.md)  
  
-   [sizeof — operator](../cpp/sizeof-operator.md)  
  
-   [__uuidof operator](../cpp/uuidof-operator.md)  
  
-   [__alignof operator](../cpp/alignof-operator.md)  
  
-   [New — operator](../cpp/new-operator-cpp.md)  
  
-   [delete — operator](../cpp/delete-operator-cpp.md)  
  
 Te operatory mają łączność od prawej do lewej. Wyrażenie jednoargumentowe generalnie wymagają składni, który poprzedza przyrostka lub wyrażenie podstawowe.  
  
 Poniżej przedstawiono możliwe formy wyrażeń jednoargumentowy.  
  
-   *wyrażeniem przyrostkowym*  
  
-   `++` *wyrażenie jednoargumentowe*  
  
-   `--` *wyrażenie jednoargumentowe*  
  
-   *operator jednoargumentowy* *wyrażenie cast*  
  
-   **Operator sizeof** *jednoargumentowe wyrażenie*  
  
-   `sizeof(` *Nazwa typu* `)`  
  
-   `decltype(` *Wyrażenie* `)`  
  
-   *wyrażenie alokacji*  
  
-   *wyrażenie cofania alokacji*  
  
 Wszelkie *wyrażeniem przyrostkowym* jest uważany za *jednoargumentowe wyrażenie*, i ponieważ dowolne wyrażenie głównej jest uznawana za *postfix-expression*, jest dowolnego wyrażenia podstawowe uważane za *jednoargumentowe wyrażenie* również. Aby uzyskać więcej informacji, zobacz [wyrażenia przyrostkowe](../cpp/postfix-expressions.md) i [wyrażenia podstawowe](../cpp/primary-expressions.md).  
  
 A *operatora jednoargumentowego* składa się z co najmniej jedną z następujących symboli: `* & + - ! ~`  
  
 *Wyrażenie cast* wyrażenie jednoargumentowe z opcjonalnych rzutowania, aby zmienić typ. Aby uzyskać więcej informacji, zobacz [Operator rzutowania: ()](../cpp/cast-operator-parens.md).  
  
 *Wyrażenie* może być każdym wyrażeniem. Aby uzyskać więcej informacji, zobacz [wyrażenia](../cpp/expressions-cpp.md).  
  
 *Wyrażenie alokacji* odwołuje się do **nowe** operatora. *Wyrażenie dezalokacji* odwołuje się do **Usuń** operatora. Aby uzyskać więcej informacji zobacz linki we wcześniejszej części tego tematu.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy wyrażeń](../cpp/types-of-expressions.md)