---
title: '&lt;memory_resource&gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: de88feb691d0ec1bc9bf9b9dc2bc40cbc31a1cfe
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831050"
---
# <a name="ltmemory_resourcegt"></a>&lt;memory_resource&gt;

Definiuje szablon klasy kontenera memory_resource i jego szablony pomocnicze.

## <a name="syntax"></a>Składnia

```cpp
#include <memory_resource>
```

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[operator! =](../standard-library/memory-resource-operators.md#op_neq)|Testuje, czy obiekt memory_resource po lewej stronie operatora nie jest równy obiektowi memory_resource po prawej stronie.|
|[operator = =](../standard-library/memory-resource-operators.md#op_eq_eq)|Testuje, czy obiekt memory_resource po lewej stronie operatora jest równy obiektowi memory_resource po prawej stronie.|

### <a name="specialized-template-functions"></a>Specialized Template — Funkcje

|Nazwa|Opis|
|-|-|
|[polymorphic_allocator](../standard-library/memory-resource-functions.md#poly_alloc)||

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[get_default_resource](../standard-library/memory-resource-functions.md#get_default)||
|[new_delete_resource](../standard-library/memory-resource-functions.md#new_delete)||
|[null_memory_resource](../standard-library/memory-resource-functions.md#null_memory)||
|[set_default_resource](../standard-library/memory-resource-functions.md#set_default)||

### <a name="classes-and-structs"></a>Klasy i struktury

|Nazwa|Opis|
|-|-|
|[Klasa memory_resource](../standard-library/memory-resource-class.md)||
|[Klasa monotonic_buffer_resource](../standard-library/monotonic-buffer-resource-class.md)||
|[Struktura pool_options](../standard-library/pool-options-structure.md)||
|[Klasa synchronized_pool_resource](../standard-library/synchronized-pool-resource-class.md)||
|[Klasa unsynchronized_pool_resource](../standard-library/unsynchronized-pool-resource-class.md)||

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
