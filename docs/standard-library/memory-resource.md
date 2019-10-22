---
title: '&lt;memory_resource &gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: 752396bb06b292ce29b7c6cd292287955b6066a7
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687711"
---
# <a name="ltmemory_resourcegt"></a>&lt;memory_resource &gt;

Definiuje szablon klasy kontenera memory_resource i jego szablony pomocnicze.

## <a name="syntax"></a>Składnia

```cpp
#include <memory_resource>
```

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator!=](../standard-library/memory-resource-operators.md#op_neq)|Testuje, czy obiekt memory_resource po lewej stronie operatora nie jest równy obiektowi memory_resource po prawej stronie.|
|[operator = =](../standard-library/memory-resource-operators.md#op_eq_eq)|Testuje, czy obiekt memory_resource po lewej stronie operatora jest równy obiektowi memory_resource po prawej stronie.|

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
|[Klasa memory_resource](../standard-library/memory-resource-class.md)||
|[Klasa monotonic_buffer_resource](../standard-library/monotonic-buffer-resource-class.md)||
|[pool_options, struktura](../standard-library/pool-options-structure.md)||
|[Klasa synchronized_pool_resource](../standard-library/synchronized-pool-resource-class.md)||
|[Klasa unsynchronized_pool_resource](../standard-library/unsynchronized-pool-resource-class.md)||

## <a name="see-also"></a>Zobacz także

[Odwołania do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md) \
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
