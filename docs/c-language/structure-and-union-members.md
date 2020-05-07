---
title: Elementy członkowskie struktury i złożenia
ms.date: 11/04/2016
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
ms.openlocfilehash: b22f5a29a4dc088ea4f3db863d635badee048d2c
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825694"
---
# <a name="structure-and-union-members"></a>Elementy członkowskie struktury i złożenia

„Wyrażenie wyboru elementu członkowskiego” dotyczy elementów członkowskich struktur i unii. Takie wyrażenie ma wartość i typ wybranego elementu członkowskiego.

> *wyrażenie przyrostkowe* **.** *identyfikatora*\
> **->** *Identyfikator* *wyrażenia przyrostkowego*

Poniższa lista opisuje dwie formy wyrażeń wyboru elementów członkowskich:

1. W pierwszej postaci *wyrażenie przyrostkowe* reprezentuje wartość typu **struct** lub **Union** , a *Identyfikator* zawiera nazwę elementu członkowskiego określonej struktury lub Unii. Wartość operacji to *Identyfikator* i jest l-wartością, jeśli *przyrostke wyrażenie* jest l-wartością. Aby uzyskać więcej informacji [, zobacz wyrażenia wartości L i R](../c-language/l-value-and-r-value-expressions.md) .

1. W drugiej postaci *wyrażenie przyrostkowe* reprezentuje wskaźnik do struktury lub Unii, a *Identyfikator* zawiera nazwę elementu członkowskiego określonej struktury lub Unii. Wartość jest równa *identyfikatorowi* i jest l-wartością.

Obie formy wyrażeń wyboru elementów członkowskich mają podobne skutki.

W rzeczywistości wyrażenie obejmujące operator wyboru elementu członkowskiego (**->**) jest skrótową wersją wyrażenia przy użyciu kropki (**.**), jeśli wyrażenie przed kropką składa się z operatora pośredniego (<strong>\*</strong>) zastosowanego do wartości wskaźnika. Zatem

```cpp
expression->identifier
```

jest równoważny

```cpp
(*expression).identifier
```

gdy *wyrażenie* jest wartością wskaźnika.

## <a name="examples"></a>Przykłady

Następujące przykłady dotyczą niniejszej deklaracji struktury. Aby uzyskać informacje o operatorze pośredni (<strong>\*</strong>) używanym w tych przykładach, zobacz [Operatory pośrednie i Address-of](../c-language/indirection-and-address-of-operators.md).

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

W tym przykładzie wyrażenie `item.sp` wskaźnika jest używane z operatorem wyboru elementu członkowskiego (**->**) do przypisywania wartości do elementu członkowskiego. `a`

```
list[8].b = 12;
```

Ta instrukcja pokazuje, jak wybrać dany element członkowski struktury z tablicy struktur.

## <a name="see-also"></a>Zobacz też

[Operatory dostępu do składowych: . i ->](../cpp/member-access-operators-dot-and.md)
