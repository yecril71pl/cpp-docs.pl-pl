---
title: hash — Struktura
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::hash
ms.assetid: e5a41202-ef3b-45d0-b3a7-4c2dbdc0487a
ms.openlocfilehash: b8484c8987534051c79ea02a1f87f0df1cd1f027
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456358"
---
# <a name="hash-structure"></a>hash — Struktura

Klasa szablonu definiuje jej metodę jako zwracaną `val.hash_code()`. Metoda definiuje funkcję mieszania, która jest używana do mapowania wartości typu [type_index](../standard-library/type-index-class.md) na rozkład wartości indeksu.

## <a name="syntax"></a>Składnia

```cpp
template <> struct hash<type_index>
: public unary_function<type_index, size_t>
{ // hashes a typeinfo object
    size_t operator()(type_index val) const;
};
```

## <a name="specialized-types"></a>Typy wyspecjalizowane

### <a name="system_error"></a>\<system_error >

```cpp
template <class T> struct hash;
template <> struct hash<error_code>;
template <> struct hash<error_condition>;
```

## <a name="see-also"></a>Zobacz także

[\<typeindex>](../standard-library/typeindex.md)
