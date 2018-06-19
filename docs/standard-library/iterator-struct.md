---
title: Iterator — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xutility/std::iterator
dev_langs:
- C++
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9cd414e2e6f23cb2fe44e6de4b5f53b33ef3555
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857886"
---
# <a name="iterator-struct"></a>iterator — Struktura

Pusty podstawowej struktury używane do zapewnienia klasy zdefiniowanej przez użytkownika iteratora działa poprawnie z **iterator_trait**s.

## <a name="syntax"></a>Składnia

```cpp
struct iterator {
   typedef Category iterator_category;
   typedef Type value_type;
   typedef Distance difference_type;
   typedef Distance distance_type;
   typedef Pointer pointer;
   typedef Reference reference;
   };
```

## <a name="remarks"></a>Uwagi

Struktura szablonu służy jako typu podstawowego dla wszystkich Iteratory. Definiowanie typów elementów członkowskich

- `iterator_category` (synonim parametru szablonu `Category`).

- `value_type` (synonim parametru szablonu **typu**).

- `difference_type` (synonim parametru szablonu `Distance`).

- `distance_type` (synonim parametru szablonu `Distance`)

- `pointer` (synonim parametru szablonu `Pointer`).

- `reference` (synonim parametru szablonu `Reference`).

Należy pamiętać, że `value_type` nie powinien być typu stałej, nawet jeśli **wskaźnika** punkty na obiekt const **typu** i odwołanie określa obiekt const **typu**.

## <a name="example"></a>Przykład

Zobacz [iterator_traits](../standard-library/iterator-traits-struct.md) przykład sposobu deklarowanie i użycie typów w klasie podstawowej iteratora.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iteratora >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
