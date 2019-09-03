---
title: pointers_to_members, pragma
ms.date: 08/29/2019
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
ms.openlocfilehash: fb5b277252b6c1422a87c5f2a2e2b7230ec49632
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219064"
---
# <a name="pointers_to_members-pragma"></a>pointers_to_members, pragma

**C++Specjalne**

Określa, czy wskaźnik do składowej klasy może być zadeklarowany przed jego definicją klasy skojarzonej. Służy do kontrolowania rozmiaru wskaźnika i kodu wymaganego do interpretacji wskaźnika.

## <a name="syntax"></a>Składnia

> **#pragma pointers_to_members (** *wskaźnik — deklaracja* [ **,** *najbardziej ogólna — reprezentacja* ])

## <a name="remarks"></a>Uwagi

Można umieścić **pointers_to_members** pragmę w pliku źródłowym jako alternatywę dla opcji kompilatora [/VMB lub/VMG](../build/reference/vmb-vmg-representation-method.md) lub [słowo kluczowe dziedziczenia](../cpp/inheritance-keywords.md).

Argument *deklaracji wskaźnika* określa, czy zadeklarowano wskaźnik do składowej przed lub po definicji powiązanej funkcji. Argument *deklaracji wskaźnika* jest jednym z dwóch następujących symboli:

| Argument | Komentarze |
|--------------|--------------|
| **full_generality** | Generuje bezpieczny, czasem nieoptymalny kod. Użyj **full_generality** , jeśli dowolny wskaźnik do składowej jest zadeklarowany przed definicją klasy skojarzonej. Ten argument zawsze używa reprezentacji wskaźnika określonej przez argument z *największą ogólną* reprezentacją. Równoważny z /vmg. |
| **best_case** | Generuje bezpieczny, optymalny kod przy użyciu reprezentacji najlepszego przypadku dla wszystkich wskaźników do członków. Wymaga zdefiniowania klasy przed zadeklarowaniem wskaźnika do składowej klasy. Wartość domyślna to **best_case**. |

Argument *najbardziej ogólna reprezentacja* określa najmniejszą reprezentację wskaźnika, którą kompilator może bezpiecznie użyć, aby odwołać się do dowolnego wskaźnika do składowej klasy w jednostce translacji. Argument może być jedną z następujących wartości:

| Argument | Komentarze |
|--------------|--------------|
| **single_inheritance** | Najbardziej ogólną reprezentacją jest pojedyncze dziedziczenie, wskaźnik do funkcji członkowskiej. Powoduje błąd, jeśli model dziedziczenia definicji klasy, do której zgłaszany jest wskaźnik do składowej, jest wielokrotny lub wirtualny. |
| **multiple_inheritance** | Najbardziej ogólną reprezentacją jest wielokrotne dziedziczenie, wskaźnik do funkcji członkowskiej. Powoduje błąd, jeśli model dziedziczenia definicji klasy, do której zgłaszany jest wskaźnik do składowej, jest wirtualny. |
| **virtual_inheritance** | Najbardziej ogólną reprezentacją jest wirtualne dziedziczenie, wskaźnik do funkcji członkowskiej. Nigdy nie powoduje błędu. **virtual_inheritance** jest domyślnym argumentem, `#pragma pointers_to_members(full_generality)` gdy jest używany. |

> [!CAUTION]
> Firma Microsoft zaleca umieszczenie dyrektywy pragma **pointers_to_members** tylko w pliku kodu źródłowego, który ma mieć wpływ, i tylko po `#include` dodaniu dyrektyw. Taka praktyka zmniejsza ryzyko, że pragma wpłynie na inne pliki i przypadkowo określi wiele definicji dla tej samej zmiennej, funkcji lub nazwy klasy.

## <a name="example"></a>Przykład

```cpp
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
