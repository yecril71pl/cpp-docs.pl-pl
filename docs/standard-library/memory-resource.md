---
title: '&lt;memory_resource&gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: b5957412d2beff0dc709dc71a77834f13eeacb41
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268157"
---
# <a name="ltmemoryresourcegt"></a>&lt;memory_resource&gt;

Definiuje memory_resource klasy szablonu kontenera i jego szablonów pomocniczych.

## <a name="syntax"></a>Składnia

```cpp
#include <memory_resource>
```

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator!=](../standard-library/memory-resource-operators.md#op_neq)|Sprawdza, czy obiekt memory_resource po lewej stronie operatora nie jest równy obiektowi memory_resource po prawej stronie.|
|[operator==](../standard-library/memory-resource-operators.md#op_eq_eq)|Sprawdza, czy obiekt memory_resource po lewej stronie operatora jest równy obiektowi memory_resource po prawej stronie.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|||
|-|-|
|[polymorphic_allocator](../standard-library/memory-resource-functions.md#poly_alloc)||

### <a name="functions"></a>Funkcje

|||
|-|-|
|[get_default_resource](../standard-library/memory-resource-functions.md#get_default)||
|[new_delete_resource](../standard-library/memory-resource-functions.md#new_delete)||
|[null_memory_resource](../standard-library/memory-resource-functions.md#null_memory)||
|[set_default_resource](../standard-library/memory-resource-functions.md#set_default)||

### <a name="classes-and-structs"></a>Klasy i struktury

|||
|-|-|
|[memory_resource klasy](../standard-library/memory-resource-class.md)||
|[monotonic_buffer_resource klasy](../standard-library/monotonic-buffer-resource-class.md)||
|[pool_options — struktura](../standard-library/pool-options-structure.md)||
|[synchronized_pool_resource klasy](../standard-library/synchronized-pool-resource-class.md)||
|[unsynchronized_pool_resource klasy](../standard-library/unsynchronized-pool-resource-class.md)||

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
