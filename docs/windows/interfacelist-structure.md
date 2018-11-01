---
title: InterfaceList — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: e0dd2a39e4764d6d33c824ca0bd1e0976fbb6ee3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472453"
---
# <a name="interfacelist-structure"></a>InterfaceList — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename T, typename U>
struct InterfaceList;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Nazwa interfejsu; Pierwszy interfejs na liście cykliczne.

*U*<br/>
Nazwa interfejsu; pozostałe interfejsy na liście cykliczne.

## <a name="remarks"></a>Uwagi

Użyty do utworzenia cyklicznego listę interfejsów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`FirstT`|Synonim dla parametru szablonu *T*.|
|`RestT`|Synonim dla parametru szablonu *U*.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`InterfaceList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)