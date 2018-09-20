---
title: Interfacelisthelper — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
dev_langs:
- C++
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 87516cf45a39602bea462b8e94f17d3ef64ad0eb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431622"
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

template <
   typename T0
>
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

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)