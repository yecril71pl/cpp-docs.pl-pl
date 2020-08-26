---
title: '&lt;span&gt;'
ms.date: 05/28/2020
f1_keywords:
- <span>
helpviewer_keywords:
- span header
ms.openlocfilehash: 7d21023c90472e5c2e1b28d9fa85e517da4a21ae
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846189"
---
# <a name="ltspangt"></a>&lt;span&gt;

A `span` to widok nad ciągłą sekwencją obiektów. Zapewnia szybki i bezpieczny dostęp. W przeciwieństwie do `vector` lub `array` , nie jest to "własne" elementy, do których zapewnia dostęp.

Aby uzyskać szczegółowe informacje, zobacz [Klasa span](span-class.md) . Oto przykład sposobu użycia zakresu:

```cpp
#include <span>
#include <iostream>

void Show(std::span<int> someValues)
{
    // show values in reverse
    for (auto rIt = someValues.rbegin(); rIt != someValues.rend(); ++rIt)
    {
        std::cout << *rIt;
    }

    // show a subspan
    for (auto& i : someValues.subspan(1, 2))
    {
        std::cout << i;
    }
}

int main()
{
    int numbers[]{ 0,1,2,3,4 };
    Show(numbers); // note conversion from array to span
}
```

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<span>

**Przestrzeń nazw:** std

**Opcja kompilatora:** /std: c + + Najnowsza

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|-|:-|
|[span](span-class.md)| Zapewnia widok nad ciągłą sekwencją obiektów. |

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|:-|
|[operator =](span-class.md#op_eq)| Przypisanie zakresu |
|[zakład\[\]](span-class.md#op_at)| Dostęp do elementu |

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|:-|
| [as_bytes](span-functions.md#as_bytes)| Pobierz bazowe bajty tylko do odczytu z zakresu. |
| [as_writable_bytes](span-functions.md#as_writable_bytes) | Pobierz bazowe bajty zakresu. |

### <a name="constants"></a>Stałe

|Nazwa|Opis|
|-|:-|
| **dynamic_extent** | Wskazuje, że rozmiar zakresu jest określany w czasie wykonywania, a nie w czasie kompilacji. Gdy liczba elementów w zakresie jest znana w czasie kompilacji, zostanie określona jako `Extent` parametr szablonu. Gdy liczba nie jest znana do czasu wykonania, należy `dynamic_extent` zamiast tego określić. |

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
