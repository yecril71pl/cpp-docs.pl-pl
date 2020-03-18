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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418336"
---
# <a name="boolstruct-structure"></a>BoolStruct — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Uwagi

Struktura `BoolStruct` określa, czy `ComPtr` zarządza okresem istnienia obiektu w interfejsie. `BoolStruct` jest używany wewnętrznie przez operator [BoolType ()](comptr-class.md#operator-microsoft-wrl-details-booltype) .

## <a name="members"></a>Members

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

Name (Nazwa)                          | Opis
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[BoolStruct:: member](#member) | Określa, że [ComPtr](comptr-class.md) ma wartość, lub nie, zarządzanie okresem istnienia obiektu w interfejsie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`BoolStruct`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Internal. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="member"></a>BoolStruct:: member

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
int Member;
```

### <a name="remarks"></a>Uwagi

Określa, że [ComPtr](comptr-class.md) ma wartość, lub nie, zarządzanie okresem istnienia obiektu w interfejsie.
