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
ms.openlocfilehash: cdec425e317585abbd9730447e2c4fbb19b8250a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58787360"
---
# <a name="boolstruct-structure"></a>BoolStruct — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Uwagi

`BoolStruct` Definiuje strukturę czy `ComPtr` Zarządzanie okresem istnienia interfejsu. `BoolStruct` jest używana wewnętrznie przez [BoolType()](comptr-class.md#operator-microsoft-wrl-details-booltype) operatora.

## <a name="members"></a>Elementy członkowskie

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

Nazwa                          | Opis
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[BoolStruct::Member](#member) | Określa, że [ComPtr](comptr-class.md) jest lub nie jest dostępna, zarządzanie okresem istnienia obiektu interfejsu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`BoolStruct`

## <a name="requirements"></a>Wymagania

**Nagłówek:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="member"></a>BoolStruct::Member

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
int Member;
```

### <a name="remarks"></a>Uwagi

Określa, że [ComPtr](comptr-class.md) jest lub nie jest dostępna, zarządzanie okresem istnienia obiektu interfejsu.
