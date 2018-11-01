---
title: hash — Struktura
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::hash
ms.assetid: e5a41202-ef3b-45d0-b3a7-4c2dbdc0487a
ms.openlocfilehash: ba05d70692b2f85c1a14f319fb1e92dcadc0ccce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582263"
---
# <a name="hash-structure"></a>hash — Struktura

Klasa szablon definiuje sposób jej powrotu `val.hash_code()`. Metoda określa funkcję mieszania, która służy do mapowania wartości typu [type_index](../standard-library/type-index-class.md) do rozłożenia wartości indeksu.

## <a name="syntax"></a>Składnia

```cpp
template <>
struct hash<type_index>
: public unary_function<type_index, size_t>
{ // hashes a typeinfo object
    size_t operator()(type_index val) const;

};
```

## <a name="see-also"></a>Zobacz także

[\<typeindex >](../standard-library/typeindex.md)<br/>
