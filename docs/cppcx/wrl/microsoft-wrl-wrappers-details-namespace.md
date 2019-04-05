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
ms.openlocfilehash: deccd4519b2ddf18725dca5af13b94ac79d6e280
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038725"
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
|[SyncLockT — Klasa](synclockt-class.md)|Reprezentuje typ, który może zająć wyłączne lub współużytkować własność zasobu.|
|[SyncLockWithStatusT — Klasa](synclockwithstatust-class.md)|Reprezentuje typ, który może zająć wyłączne lub współużytkować własność zasobu.|

### <a name="methods"></a>Metody

|Nazwa|Opis|
|----------|-----------------|
|[CompareStringOrdinal — Metoda](comparestringordinal-method.md)|Porównuje dwa określone `HSTRING` obiekty i zwraca liczbę całkowitą, która wskazuje ich względne położenie w kolejności sortowania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL::Wrappers — Przestrzeń nazw](microsoft-wrl-wrappers-namespace.md)