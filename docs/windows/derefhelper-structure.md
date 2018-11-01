---
title: DerefHelper — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::DerefHelper
helpviewer_keywords:
- DerefHelper structure
ms.assetid: 86ded58b-c3ee-4a4f-bb86-4f67b895d427
ms.openlocfilehash: 7e9de446fdf18b3cf92cc438e421287c8fcfc29f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450205"
---
# <a name="derefhelper-structure"></a>DerefHelper — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
struct DerefHelper;

template <typename T>
struct DerefHelper<T*>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Parametr szablonu.

## <a name="remarks"></a>Uwagi

Reprezentuje wskaźnik wyłuskiwany `T*` parametru szablonu.

**Derefhelper —** jest używana w wyrażeniu, takich jak: `ComPtr<Details::DerefHelper<ProgressTraits::Arg1Type>::DerefType> operationInterface;`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`DerefType`|Identyfikator parametru szablonu wyłuskiwany `T*`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`DerefHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)