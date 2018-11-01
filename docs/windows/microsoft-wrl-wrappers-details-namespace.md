---
title: Microsoft::WRL::Wrappers::Details — Przestrzeń nazw
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details
- internal/Microsoft::WRL::Details
- async/Microsoft::WRL::Details
- corewrappers/Microsoft::WRL::Wrappers::Details
- client/Microsoft::WRL::Details
- module/Microsoft::WRL::Details
- event/Microsoft::WRL::Details
helpviewer_keywords:
- Details namespace
ms.assetid: 6d3f04ac-9b53-4a82-a188-a85309ec34a4
ms.openlocfilehash: 09f3fd1011b05e9aee9816663cb5bd1d9e0081e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431879"
---
# <a name="microsoftwrlwrappersdetails-namespace"></a>Microsoft::WRL::Wrappers::Details — Przestrzeń nazw

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
namespace Microsoft::WRL::Wrappers::Details;
```

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[SyncLockT, klasa](../windows/synclockt-class.md)|Reprezentuje typ, który może zająć wyłączne lub współużytkować własność zasobu.|
|[SyncLockWithStatusT, klasa](../windows/synclockwithstatust-class.md)|Reprezentuje typ, który może zająć wyłączne lub współużytkować własność zasobu.|

### <a name="methods"></a>Metody

|Nazwa|Opis|
|----------|-----------------|
|[CompareStringOrdinal, metoda](../windows/comparestringordinal-method.md)|Porównuje dwa określone `HSTRING` obiekty i zwraca liczbę całkowitą, która wskazuje ich względne położenie w kolejności sortowania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)