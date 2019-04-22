---
title: InterfaceListHelper — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
ms.openlocfilehash: 03bfed00147daef22fe91e6f061ea6720834090f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025114"
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

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)