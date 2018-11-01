---
title: hash — Struktura (standardowa biblioteka C++) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
f1_keywords:
- thread/std::hash
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
ms.openlocfilehash: bb230d401d5061f4951f8007f93c3a28ce3dab03
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579872"
---
# <a name="hash-structure-c-standard-library"></a>hash — Struktura (standardowa biblioteka C++)

Definiuje funkcja elementu członkowskiego, która zwraca wartość, która jednoznacznie jest określana przez `Val`. Funkcja elementu członkowskiego zdefiniowano [skrótu](../standard-library/hash-class.md) funkcja, która jest odpowiednia do mapowania wartości typu `thread::id` do rozłożenia wartości indeksu.

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

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<Wątek >](../standard-library/thread.md)<br/>
[unary_function, struktura](../standard-library/unary-function-struct.md)<br/>
