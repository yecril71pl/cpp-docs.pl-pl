---
title: '&lt;nowe&gt; definicje typów'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 80123bc35422984ef92bdba6da45052d3461b1d7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245157"
---
# <a name="ltnewgt-typedefs"></a>&lt;nowe&gt; definicje typów

## <a name="hardware_constructive_interference_size"></a> hardware_constructive_interference_size

```cpp
inline constexpr size_t hardware_constructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Uwagi

Ta liczba jest maksymalny zalecany rozmiar pamięci ciągłej zajmowane przez dwa obiekty, które uzyskują dostęp przy użyciu danych czasowych miejscowość współbieżnych wątków. Jest co najmniej `alignof(max_align_t)`.

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

## <a name="hardware_destructive_interference_size"></a> hardware_destructive_interference_size

```cpp
inline constexpr size_t hardware_destructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Uwagi

Ta liczba jest minimalna zalecana przesunięcie pomiędzy dwoma obiektami jednocześnie uzyskać dostęp, aby uniknąć spadku wydajności dodatkowe z powodu rywalizacji wynikające z wdrożenia. Jest co najmniej `alignof(max_align_t)`.

### <a name="example"></a>Przykład

```cpp
struct keep_apart {
    alignas(hardware_destructive_interference_size) atomic<int> cat;
    alignas(hardware_destructive_interference_size) atomic<int> dog;
};
```

## <a name="new_handler"></a> new_handler

Punkty typu do funkcji odpowiedni do użycia jako nowy program obsługi.

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>Uwagi

Tego rodzaju funkcji obsługi jest wywoływana przez **nowy operator** lub `operator new[]` kiedy nie może spełnić żądania dodatkowego miejsca do magazynowania.

### <a name="example"></a>Przykład

Zobacz [set_new_handler](../standard-library/new-functions.md#set_new_handler) dla przykłady dotyczące używania `new_handler` jako wartości zwracanej.
