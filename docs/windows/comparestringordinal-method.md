---
title: CompareStringOrdinal, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
dev_langs:
- C++
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9fba5ff2db133d7a510499bd79de8bb77119eb79
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387214"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal — Metoda

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
inline INT32 CompareStringOrdinal(
   HSTRING lhs,
   HSTRING rhs)  
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*<br/>
Pierwszy obiekt HSTRING do porównania.

*RHS*<br/>
Drugi obiekt HSTRING do porównania.

## <a name="return-value"></a>Wartość zwracana

|Wartość|Warunek|
|-----------|---------------|
|-1|*Lewa strona reguły przepisywania* jest mniejsza niż *rhs*.|
|0|*Lewa strona reguły przepisywania* jest równa *rhs*.|
|1|*Lewa strona reguły przepisywania* jest większa niż *rhs*.|

## <a name="remarks"></a>Uwagi

Porównuje dwa obiekty HSTRING określonego i zwraca liczbę całkowitą, która wskazuje ich względne położenie w kolejności sortowania.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Wrappers::Details, przestrzeń nazw](../windows/microsoft-wrl-wrappers-details-namespace.md)