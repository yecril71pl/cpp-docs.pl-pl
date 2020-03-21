---
title: '&lt;nowe&gt; Typedefs'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 30bd84a1d69d3d8f24cd36450a18b23b92c3c2c6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076423"
---
# <a name="ltnewgt-typedefs"></a>&lt;nowe&gt; Typedefs

## <a name="hardware_constructive_interference_size"></a><a name="hardware_constructive_interference_size"></a>hardware_constructive_interference_size

```cpp
inline constexpr size_t hardware_constructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Uwagi

Ta liczba jest maksymalnym zalecanym rozmiarem ciągłej pamięci, która jest zajęta przez dwa obiekty, do których jest uzyskiwany czas niedostępności przez współbieżne wątki. Powinien być co najmniej `alignof(max_align_t)`.

### <a name="example"></a>Przykład

```cpp
struct together {
    atomic<int> dog;
    int puppy;
};

struct kennel {
    // Other data members...
    alignas(sizeof(together)) together pack;
    // Other data members...
};

static_assert(sizeof(together) <= hardware_constructive_interference_size);
```

## <a name="hardware_destructive_interference_size"></a><a name="hardware_destructive_interference_size"></a>hardware_destructive_interference_size

```cpp
inline constexpr size_t hardware_destructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Uwagi

Ta liczba jest minimalnym zalecanym przesunięciem między dwoma dostępnymi jednocześnie obiektami, aby uniknąć dodatkowego obniżenia wydajności z powodu rywalizacji wprowadzonej przez implementację. Powinien być co najmniej `alignof(max_align_t)`.

### <a name="example"></a>Przykład

```cpp
struct keep_apart {
    alignas(hardware_destructive_interference_size) atomic<int> cat;
    alignas(hardware_destructive_interference_size) atomic<int> dog;
};
```

## <a name="new_handler"></a><a name="new_handler"></a>new_handler

Typ wskazuje funkcję odpowiednią do użycia jako nowy program obsługi.

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>Uwagi

Ten typ funkcji obsługi jest wywoływany przez **operator new** lub `operator new[]`, gdy nie mogą one spełnić żądania dodatkowego magazynu.

### <a name="example"></a>Przykład

Zobacz [set_new_handler](../standard-library/new-functions.md#set_new_handler) , aby zapoznać się z przykładem, korzystając z `new_handler` jako wartości zwracanej.
