---
title: Składowe struktury i złożenia | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c244a55b4e0ebdfadf13e5ee0a3120f024d318af
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099671"
---
# <a name="structure-and-union-members"></a>Elementy członkowskie struktury i złożenia

„Wyrażenie wyboru elementu członkowskiego” dotyczy elementów członkowskich struktur i unii. Takie wyrażenie ma wartość i typ wybranego elementu członkowskiego.

> *wyrażeniem przyrostkowym* **.** *Identyfikator*
> *wyrażeniem przyrostkowym* ** -> ** *identyfikator*

Poniższa lista opisuje dwie formy wyrażeń wyboru elementów członkowskich:

1. W pierwszej formie *wyrażeniem przyrostkowym* reprezentuje wartość **struktury** lub **Unii** typu, i *identyfikator* nazwy członka określonej struktury lub Unii. Wartością operacji jest *identyfikator* i jest l wartością, jeśli *wyrażeniem przyrostkowym* jest l wartością. Zobacz [wyrażenia wartości L i r](../c-language/l-value-and-r-value-expressions.md) Aby uzyskać więcej informacji.

1. W drugim formularzu *wyrażeniem przyrostkowym* reprezentuje wskaźnik do struktury lub Unii, i *identyfikator* nazw jest członkiem określonej struktury lub Unii. Wartość jest *identyfikator* i jest l wartością.

Obie formy wyrażeń wyboru elementów członkowskich mają podobne skutki.

W rzeczywistości, wyrażenie obejmujące operator wyboru składowej (**->**) jest wersją skróconą wyrażenia używającego kropki (**.**) Jeśli wyrażenie przed kropką składa się z operator pośredni (<strong>\*</strong>) stosowany do wartości wskaźnika. W związku z tym,

```cpp
expression->identifier
```

odpowiada wyrażeniu

```cpp
(*expression).identifier
```

gdy *wyrażenie* jest wartością wskaźnika.

## <a name="examples"></a>Przykłady

Następujące przykłady dotyczą niniejszej deklaracji struktury. Aby uzyskać informacje dotyczące operatora pośredniego (<strong>\*</strong>) używanego w tych przykładach, zobacz [pośredni i Address-of operatory](../c-language/indirection-and-address-of-operators.md).

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

W tym przykładzie wyrażenie wskaźnika `item.sp` jest używany z operatorem wyboru elementów członkowskich (**->**) do przypisania wartości do elementu członkowskiego `a`.

```
list[8].b = 12;
```

Ta instrukcja pokazuje, jak wybrać dany element członkowski struktury z tablicy struktur.

## <a name="see-also"></a>Zobacz też

[Operatory dostępu do składowych: . i ->](../cpp/member-access-operators-dot-and.md)