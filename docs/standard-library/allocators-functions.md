---
title: '&lt;&gt; makra przydzieleń'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::ALLOCATOR_DECL
- allocators/std::CACHE_CHUNKLIST
- allocators/std::CACHE_FREELIST
- allocators/std::CACHE_SUBALLOC
- allocators/std::SYNC_DEFAULT
ms.assetid: 9cb5ee07-1ff9-4594-ae32-3c8c6efb511a
helpviewer_keywords:
- std::ALLOCATOR_DECL [C++]
- std::CACHE_CHUNKLIST [C++]
- std::CACHE_FREELIST [C++]
- std::CACHE_SUBALLOC [C++]
- std::SYNC_DEFAULT [C++]
ms.openlocfilehash: 10cd1d51c2cd6053dcbaa0f5bf1548f80ed01659
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448237"
---
# <a name="ltallocatorsgt-macros"></a>&lt;&gt; makra przydzieleń

||||
|-|-|-|
|[ALLOCATOR_DECL](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[CACHE_FREELIST](#cache_freelist)|
|[CACHE_SUBALLOC](#cache_suballoc)|[SYNC_DEFAULT](#sync_default)|

## <a name="allocator_decl"></a>ALLOCATOR_DECL

Zwraca klasę szablonu alokatora.

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>Uwagi

Makro daje definicję `template <class Type> class name {.....}` szablonu i `template <> class name<void> {.....}` specjalizację, która wspólnie definiuje klasę szablonu alokatora, która używa filtru `sync` synchronizacji i pamięci podręcznej typu `cache`.

W przypadku kompilatorów, które mogą skompilować ponownie powiązanie, wynikowa definicja szablonu wygląda następująco:

```cpp
struct rebind
   {    /* convert a name<Type> to a name<Other> */
   typedef name<Other> other;
   };
```

W przypadku kompilatorów, które nie mogą skompilować ponownie powiązania, wynikowa definicja szablonu wygląda następująco:

```cpp
template <class Type<class name
    : public stdext::allocators::allocator_base<Type,
    sync<stdext::allocators::rts_alloc<cache>>>
{
public:
    name() {}
    template <class Other>
    name(const name<Other>&) {}
    template <class Other>
    name& operator= (const name<Other>&)
    {
        return *this;
    }
};
```

## <a name="cache_chunklist"></a>CACHE_CHUNKLIST

Daje w wyniku. `stdext::allocators::cache_chunklist<sizeof(Type)>`

```cpp
#define CACHE_CHUNKLIST <cache_class>
```

### <a name="remarks"></a>Uwagi

## <a name="cache_freelist"></a>CACHE_FREELIST

Daje w wyniku. `stdext::allocators::cache_freelist<sizeof(Type), max>`

```cpp
#define CACHE_FREELIST(max) <cache_class>
```

### <a name="remarks"></a>Uwagi

## <a name="cache_suballoc"></a>  CACHE_SUBALLOC

Daje w wyniku. `stdext::allocators::cache_suballoc<sizeof(Type)>`

```cpp
#define CACHE_SUBALLOC <cache_class>
```

### <a name="remarks"></a>Uwagi

## <a name="sync_default"></a>  SYNC_DEFAULT

Zwraca filtr synchronizacji.

```cpp
#define SYNC_DEFAULT <sync_template>
```

### <a name="remarks"></a>Uwagi

Jeśli kompilator obsługuje Kompilowanie aplikacji wielowątkowych i wielowątkowych, w przypadku aplikacji jednowątkowych makro daje `stdext::allocators::sync_none`w wyniku wszystkie inne przypadki. `stdext::allocators::sync_shared`

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)
