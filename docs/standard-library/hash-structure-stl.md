---
title: hash — Struktura (standardowa biblioteka C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- thread/std::hash
dev_langs:
- C++
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f2e9fdbef911a0160ff42925a9c7984f0211069
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="hash-structure-c-standard-library"></a>hash — Struktura (standardowa biblioteka C++)

Definiuje funkcję elementu członkowskiego, która zwraca wartość, która unikatowo jest określany przez `Val`. Definiuje funkcję elementu członkowskiego [skrótu](../standard-library/hash-class.md) funkcji, które jest odpowiednie dla wartości mapowanie typu `thread::id` dystrybucji wartości indeksu.

## <a name="syntax"></a>Składnia

```cpp
template <>
struct hash<thread::id> :
    public unary_function<thread::id, size_t>
{
    size_t operator()(thread::id Val) const;


};
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wątku >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<Wątek >](../standard-library/thread.md)<br/>
[unary_function, struktura](../standard-library/unary-function-struct.md)<br/>
