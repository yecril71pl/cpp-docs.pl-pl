---
title: hash — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- typeindex/std::hash
dev_langs:
- C++
ms.assetid: e5a41202-ef3b-45d0-b3a7-4c2dbdc0487a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82684ac8f2dcd0b8e1b76f04ace8d51051681bd0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843655"
---
# <a name="hash-structure"></a>hash — Struktura

Klasa szablon definiuje jej metodę jako zwracanie `val.hash_code()`. Metoda definiuje funkcji skrótu, który jest używany do mapowania wartości typu [type_index —](../standard-library/type-index-class.md) dystrybucji wartości indeksu.

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
