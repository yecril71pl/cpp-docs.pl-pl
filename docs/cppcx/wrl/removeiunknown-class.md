---
title: RemoveIUnknown — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: cfcdefbb8d7cd12d2ebf99710f595fdd2fc16f76
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213619"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown — Klasa

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
struct RemoveIUnknown;

template <typename T>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Klasa.

## <a name="remarks"></a>Uwagi

Tworzy typ, który jest odpowiednikiem typu `IUnknown`, ale ma niewirtualne `QueryInterface`, `AddRef`i `Release` funkcje składowe.

Domyślnie metody COM zapewniają metody wirtualne `QueryInterface`, `AddRef`i `Release`. Niemniej jednak `ComPtr` nie wymagają nakładów związanych z metodami wirtualnymi. `RemoveIUnknown` eliminuje to narzuty, zapewniając prywatne, niewirtualne `QueryInterface`, `AddRef`i metody `Release`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`ReturnType`|Synonim dla typu, który jest odpowiednikiem parametru szablonu *T* , ale zawiera niewirtualne elementy członkowskie `IUnknown`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`T`

`RemoveIUnknown`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Client. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)
