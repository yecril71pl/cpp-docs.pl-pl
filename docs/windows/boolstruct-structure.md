---
title: BoolStruct — Struktura
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
- internal/Microsoft::WRL::Details::BoolStruct::Member
helpviewer_keywords:
- Microsoft::WRL::Details::BoolStruct structure
- Microsoft::WRL::Details::BoolStruct::Member data member
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
ms.openlocfilehash: d79ea93bf95040efe79e3e3c57ceb3397fd257de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643407"
---
# <a name="boolstruct-structure"></a>BoolStruct — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Uwagi

`BoolStruct` Definiuje strukturę czy `ComPtr` Zarządzanie okresem istnienia interfejsu. `BoolStruct` jest używana wewnętrznie przez [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operatora.

## <a name="members"></a>Elementy członkowskie

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

Nazwa                          | Opis
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[BoolStruct::Member](#member) | Określa, że [ComPtr](../windows/comptr-class.md) jest lub nie jest dostępna, zarządzanie okresem istnienia obiektu interfejsu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`BoolStruct`

## <a name="requirements"></a>Wymagania

**Nagłówek:** internal.h

**Namespace:** Microsoft::wrl:: details

## <a name="member"></a>BoolStruct::Member

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
int Member;
```

### <a name="remarks"></a>Uwagi

Określa, że [ComPtr](../windows/comptr-class.md) jest lub nie jest dostępna, zarządzanie okresem istnienia obiektu interfejsu.
