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
ms.openlocfilehash: db47362096506cf1c00f1ac566565b894253d798
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157854"
---
# <a name="structure-and-union-members"></a>Elementy członkowskie struktury i złożenia

„Wyrażenie wyboru elementu członkowskiego” dotyczy elementów członkowskich struktur i unii. Takie wyrażenie ma wartość i typ wybranego elementu członkowskiego.

> *wyrażeniem przyrostkowym* **.** *Identyfikator*
> *wyrażeniem przyrostkowym* **->** *identyfikator*

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

## <a name="see-also"></a>Zobacz także

[Operatory dostępu do składowych: . i ->](../cpp/member-access-operators-dot-and.md)
