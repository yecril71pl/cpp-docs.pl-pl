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
ms.openlocfilehash: 4f2a5acf6edb824cff2121c1b6444181b5cfcf98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371849"
---
# <a name="boolstruct-structure"></a>BoolStruct — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Uwagi

Struktura `BoolStruct` określa, czy `ComPtr` zarządza okresem istnienia obiektu interfejsu. `BoolStruct`jest używany wewnętrznie przez [boolType().](comptr-class.md#operator-microsoft-wrl-details-booltype)

## <a name="members"></a>Elementy członkowskie

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

Nazwa                          | Opis
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[BoolStruct::Element członkowski](#member) | Określa, że [program ComPtr](comptr-class.md) zarządza okresem istnienia obiektu interfejsu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`BoolStruct`

## <a name="requirements"></a>Wymagania

**Nagłówek:** internal.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="boolstructmember"></a><a name="member"></a>BoolStruct::Element członkowski

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
int Member;
```

### <a name="remarks"></a>Uwagi

Określa, że [program ComPtr](comptr-class.md) zarządza okresem istnienia obiektu interfejsu.
