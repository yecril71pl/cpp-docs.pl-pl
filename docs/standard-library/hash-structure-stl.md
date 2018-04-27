---
title: hash — Struktura (standardowa biblioteka C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- thread/std::hash
dev_langs:
- C++
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e9898ce4415420966c4f3377865bda6346cdf67
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
