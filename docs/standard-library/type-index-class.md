---
title: type_index — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- typeindex/std::type_index
dev_langs:
- C++
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e301b8d47c1a054a5b80bff105950d876d90b047
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853999"
---
# <a name="typeindex-class"></a>type_index — Klasa

`type_index` Klasy opakowuje wskaźnik do [type_info — klasa](../cpp/type-info-class.md) ułatwiających indeksowania przez takie obiekty.

type_index — klasa {publicznego: type_index — (const type_info — & tinfo); Stała *name() char const; size_t hash_code() const bool — operator == (const type_info — & prawej) const; bool — operator! = (const type_info — & prawej) const; bool operator <(const type_ informacje o & prawej) const; bool — operator\<= (const type_info — & prawej) const; bool — operator > (const type_info — & prawej) const; bool — operator > = (const type_info — & prawej) const;};

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
[\<typeindex >](../standard-library/typeindex.md)<br/>
