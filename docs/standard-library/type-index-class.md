---
title: type_index — Klasa
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::type_index
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
ms.openlocfilehash: b30c9719957b9ffc5f3ce17692eb90c1b266ae0f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447054"
---
# <a name="typeindex-class"></a>type_index — Klasa

Klasa otacza wskaźnik do [klasy type_info](../cpp/type-info-class.md) w celu ułatwienia indeksowania przez takie obiekty. `type_index`

Klasa type_index {Public: type_index (const type_info & tInfo); const char * Name () const; size_t hash_code () const; operator bool = = (const type_info & Right) const; operator bool! = (const type_info & Right) const; operator bool < (const type_ Informacje & prawej) const; operator\<logiczny = (const type_info & Right) const; operator bool > (const type_info & Right) const; operator bool > = (const type_info & Right) const;};

Konstruktor inicjuje `ptr` się do `&tinfo`.

`name`zwraca `ptr->name()`wartość.

`hash_code`typu`ptr->hash_code().`

`operator==`zwraca `*ptr == right.ptr`wartość.

`operator!=`zwraca `!(*this == right)`wartość.

`operator<`zwraca `*ptr->before(*right.ptr)`wartość.

`operator<=`typu`!(right < *this).`

`operator>`zwraca `right < *this`wartość.

`operator>=`zwraca `!(*this < right)`wartość.

## <a name="see-also"></a>Zobacz także

[Informacje o typie w czasie wykonywania](../cpp/run-time-type-information.md)\
[\<typeindex>](../standard-library/typeindex.md)
