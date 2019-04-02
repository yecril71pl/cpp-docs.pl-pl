---
title: RemoveIUnknown — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: bfe397f64650caedab1408f1f74fabd005dd98cf
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786817"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown — Klasa

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
struct RemoveIUnknown;

template <typename T>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa.

## <a name="remarks"></a>Uwagi

Tworzy typ, który jest odpowiednikiem `IUnknown`— na podstawie typu, ale ma niewirtualne `QueryInterface`, `AddRef`, i `Release` funkcji elementów członkowskich.

Domyślnie metody COM zapewniają wirtualnego `QueryInterface`, `AddRef`, i `Release` metody. Jednak `ComPtr` nie wymaga pracy związanej z metod wirtualnych. `RemoveIUnknown` eliminuje obciążenie tego, zapewniając prywatne i niewirtualne `QueryInterface`, `AddRef`, i `Release` metody.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`ReturnType`|Synonim dla typu, który jest odpowiednikiem parametru szablonu *T* , ale ma niewirtualne `IUnknown` elementów członkowskich.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`T`

`RemoveIUnknown`

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)