---
title: iterator — Struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
ms.openlocfilehash: 1dd62a6141e690d3bd4dcad69aa107c126a0f386
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224106"
---
# <a name="iterator-struct"></a>iterator — Struktura

Pusta Struktura podstawowego, pozwala zagwarantować, że klasy zdefiniowane przez użytkownika iteratora działa poprawnie przy użyciu `iterator_trait`s.

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

Struktura szablonu służy jako typ podstawowy dla wszystkich iteratorów. Definiuje typy elementów członkowskich

- `iterator_category` (synonim dla parametru szablonu `Category`).

- `value_type` (synonim dla parametru szablonu `Type`).

- `difference_type` (synonim dla parametru szablonu `Distance`).

- `distance_type` (synonim dla parametru szablonu `Distance`)

- `pointer` (synonim dla parametru szablonu `Pointer`).

- `reference` (synonim dla parametru szablonu `Reference`).

Należy pamiętać, że `value_type` nie powinny być nawet wtedy, gdy typ stałej `pointer` punktów w obiekt **const** `Type` i odwołanie wskazuje obiekt **const** `Type`.

## <a name="example"></a>Przykład

Zobacz [iterator_traits —](../standard-library/iterator-traits-struct.md) przykładowy sposób deklarowania i korzystają z typów w klasie bazowej iteratora.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iterator >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
