---
title: DerefHelper — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::DerefHelper
helpviewer_keywords:
- DerefHelper structure
ms.assetid: 86ded58b-c3ee-4a4f-bb86-4f67b895d427
ms.openlocfilehash: 43453d3162de697fa1cfcf0581953c91bbe3934f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214048"
---
# <a name="derefhelper-structure"></a>DerefHelper — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
struct DerefHelper;

template <typename T>
struct DerefHelper<T*>;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Parametr szablonu.

## <a name="remarks"></a>Uwagi

Reprezentuje wskaźnik odwołujący do parametru szablonu `T*`.

**DerefHelper —** jest używany w wyrażeniu, takim jak: `ComPtr<Details::DerefHelper<ProgressTraits::Arg1Type>::DerefType> operationInterface;`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`DerefType`|Identyfikator dla `T*`parametru szablonu, który ma zostać odwołany.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`DerefHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Async. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)
