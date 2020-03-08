---
title: '&lt;memory_resource operatory&gt;'
ms.date: 11/04/2016
f1_keywords:
- memory_resource/std::operator!=
- memory_resource/std::operator==
helpviewer_keywords:
- std::operator!= (memory_resource)
- std::operator== (memory_resource)
ms.openlocfilehash: dd7dc3e65fe58663285433f9cbc9b64cf2b81cda
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884052"
---
# <a name="ltmemory_resourcegt-operators"></a>&lt;memory_resource operatory&gt;

## <a name="op_neq"></a>operator! =

Testuje, czy obiekt memory_resource po lewej stronie operatora nie jest równy obiektowi memory_resource po prawej stronie.

```cpp
template <class T1, class T2>
    bool operator!=(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```

## <a name="op_eq_eq"></a>operator = =

Testuje, czy obiekt memory_resource po lewej stronie operatora jest równy obiektowi memory_resource po prawej stronie.

```cpp
template <class T1, class T2>
    bool operator==(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```
