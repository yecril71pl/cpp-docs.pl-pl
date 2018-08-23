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
ms.openlocfilehash: 952de0ca136d29eb0b170856410b18a1d65120c1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612891"
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

*Lewa strona reguły przepisywania*  
Pierwszy obiekt HSTRING do porównania.

*RHS*  
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