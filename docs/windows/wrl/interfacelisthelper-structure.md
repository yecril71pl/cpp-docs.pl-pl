---
title: InterfaceListHelper — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
ms.openlocfilehash: c29a44249b432a7e0c15164307e95c51ae8b0536
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334821"
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <
    typename T0,
    typename T1 = Nil,
    typename T2 = Nil,
    typename T3 = Nil,
    typename T4 = Nil,
    typename T5 = Nil,
    typename T6 = Nil,
    typename T7 = Nil,
    typename T8 = Nil,
    typename T9 = Nil
>
struct InterfaceListHelper;

template <typename T0>
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;
```

### <a name="parameters"></a>Parametry

*T0*<br/>
Parametr szablonu, 0, który jest wymagany.

*T1*<br/>
Parametr szablonu, 1, która domyślnie jest nieokreślona.

*T2*<br/>
Parametr szablonu, 2, która domyślnie jest nieokreślona. Trzeci parametr szablonu.

*T3*<br/>
Parametr szablonu, 3, która domyślnie jest nieokreślona.

*T4*<br/>
Parametr szablonu, 4, która domyślnie jest nieokreślona.

*T5*<br/>
Parametr szablonu, 5, która domyślnie jest nieokreślona.

*T6*<br/>
Parametr szablonu, 6, która domyślnie jest nieokreślona.

*T7*<br/>
Parametr szablonu, 7, która domyślnie jest nieokreślona.

*T8*<br/>
Parametr szablonu, 8, która domyślnie jest nieokreślona.

*T9*<br/>
Parametr szablonu, 9, która domyślnie jest nieokreślona.

## <a name="remarks"></a>Uwagi

Kompilacje `InterfaceList` typu przez rekursywnie stosowanie argumentów parametru określonego szablonu.

**Interfacelisthelper —** szablon używa parametru szablonu *T0* do definiowania pierwszy element członkowski danych w `InterfaceList` struktury, a następnie rekursywnie stosuje  **Interfacelisthelper —** szablon, aby wszystkie pozostałe parametry szablonu. **Interfacelisthelper —** zatrzymuje, gdy nie ma żadnych pozostałych parametrów szablonu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`TypeT`|Synonim dla typu interfacelist —.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`InterfaceListHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)