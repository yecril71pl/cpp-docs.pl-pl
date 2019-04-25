---
title: type_index — Klasa
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::type_index
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
ms.openlocfilehash: 8807a041ab1c6ef47a9c3c12dac2688f121f6cfa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278965"
---
# <a name="typeindex-class"></a>type_index — Klasa

`type_index` Klasy otacza wskaźnik do [type_info Class](../cpp/type-info-class.md) ułatwiających indeksowania przez takie obiekty.

type_index — klasa {publicznej: type_index (const type_info & tinfo); const char *name() const; size_t hash_code() const bool — operator == (const type_info & po prawej stronie) const; bool — operator! = (const type_info & po prawej stronie) const; bool operator <(const type_ informacje o & po prawej stronie) const; bool — operator\<= (const type_info & po prawej stronie) const; bool — operator > (const type_info & po prawej stronie) const; bool — operator > = (const type_info & po prawej stronie) const;};

Konstruktor inicjuje `ptr` do `&tinfo`.

`name` Zwraca `ptr->name()`.

`hash_code` Zwraca `ptr->hash_code().`

`operator==` Zwraca `*ptr == right.ptr`.

`operator!=` Zwraca `!(*this == right)`.

`operator<` Zwraca `*ptr->before(*right.ptr)`.

`operator<=` Zwraca `!(right < *this).`

`operator>` Zwraca `right < *this`.

`operator>=` Zwraca `!(*this < right)`.

## <a name="see-also"></a>Zobacz także

[Informacje o typach uzyskiwane w czasie rzeczywistym](../cpp/run-time-type-information.md)<br/>
[\<typeindex>](../standard-library/typeindex.md)<br/>
