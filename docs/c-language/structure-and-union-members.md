---
title: Struktury i złożenia członków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- member-selection operators
- structure members, referencing
- -> operator, structure and union members
- dot operator (.)
- referencing structure members
- . operator
- operators [C], member selection
- structure member selection
ms.assetid: bb1fe304-af49-4f98-808d-afdc99b3e319
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7cf98987323b96c8b3977e9a6d2bc590e0b612b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392253"
---
# <a name="structure-and-union-members"></a>Elementy członkowskie struktury i złożenia
„Wyrażenie wyboru elementu członkowskiego” dotyczy elementów członkowskich struktur i unii. Takie wyrażenie ma wartość i typ wybranego elementu członkowskiego.  
  
```  
  
postfix-expression  
.  
identifier  
postfix-expression  
->  
identifier  
  
```  
  
 Poniższa lista opisuje dwie formy wyrażeń wyboru elementów członkowskich:  
  
1.  W formularzu pierwszy *wyrażenie przyrostek* reprezentuje wartość `struct` lub **Unii** typu, i *identyfikator* nazwy jest członkiem określonej struktury lub związku. Wartość operacji jest *identyfikator* i jest wartością l-value, jeśli *wyrażenie przyrostek* jest wartością l-value. Zobacz [wartości L i r wyrażenia](../c-language/l-value-and-r-value-expressions.md) Aby uzyskać więcej informacji.  
  
2.  W drugiej formy *wyrażenie przyrostek* reprezentuje wskaźnik do struktury lub związku, i *identyfikator* nazwy jest członkiem określonej struktury lub związku. Wartość jest *identyfikator* i jest wartością l-value.  
  
 Obie formy wyrażeń wyboru elementów członkowskich mają podobne skutki.  
  
 W rzeczywistości wyrażenie obejmujące operatora wyboru elementu członkowskiego (**->**) jest skrócona wersja wyrażenie używające okres (**.**), jeśli wyrażenie przed okresem składa się z operator pośredni (**\***) stosowane do wartości wskaźnika. W związku z tym  
  
```  
  
expression  
->  
identifier  
  
```  
  
 jest równoważny  
  
```  
  
(*  
expression  
) .  
identifier  
  
```  
  
 gdy *wyrażenie* jest wartość wskaźnika.  
  
## <a name="examples"></a>Przykłady  
 Następujące przykłady dotyczą niniejszej deklaracji struktury. Aby uzyskać informacje na temat operator pośredni (**\***) używane w tych przykładach, zobacz [operatory pośrednie i operatorów adresu](../c-language/indirection-and-address-of-operators.md).  
  
```  
struct pair   
{  
    int a;  
    int b;  
    struct pair *sp;  
} item, list[10];  
```  
  
 Wyrażenie wyboru elementów członkowskich dla struktury `item` wygląda następująco:  
  
```  
item.sp = &item;  
```  
  
 W przykładzie powyżej, adres struktury `item` jest przypisywany do elementy członkowskiego `sp` struktury. Oznacza to, że `item` zawiera wskaźnik do samego siebie.  
  
```  
(item.sp)->a = 24;  
```  
  
 W tym przykładzie wyrażenia wskaźnika `item.sp` jest używany z operatorem wyboru elementu członkowskiego (**->**) można przypisać wartości do elementu członkowskiego `a`.  
  
```  
list[8].b = 12;  
```  
  
 Ta instrukcja pokazuje, jak wybrać dany element członkowski struktury z tablicy struktur.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory dostępu do składowych: . i ->](../cpp/member-access-operators-dot-and.md)