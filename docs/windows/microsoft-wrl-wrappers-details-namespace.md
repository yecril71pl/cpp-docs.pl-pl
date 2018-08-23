---
title: Namespace Microsoft::WRL::Wrappers::details | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details
- internal/Microsoft::WRL::Details
- async/Microsoft::WRL::Details
- corewrappers/Microsoft::WRL::Wrappers::Details
- client/Microsoft::WRL::Details
- module/Microsoft::WRL::Details
- event/Microsoft::WRL::Details
dev_langs:
- C++
helpviewer_keywords:
- Details namespace
ms.assetid: 6d3f04ac-9b53-4a82-a188-a85309ec34a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3af5add0a934b59cf3027b7beb0ea000a7ae1415
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595710"
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