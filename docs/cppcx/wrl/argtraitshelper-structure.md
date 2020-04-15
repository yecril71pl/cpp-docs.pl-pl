---
title: ArgTraitsHelper — Struktura
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
- event/Microsoft::WRL::Details::ArgTraitsHelper::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraitsHelper structure
- Microsoft::WRL::Details::ArgTraitsHelper::args constant
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
ms.openlocfilehash: 4acbd9fa660f29bbaf209282ff0e90f43621574d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360768"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Interfejs delegata.

## <a name="remarks"></a>Uwagi

Pomaga zdefiniować wspólne cechy argumentów delegata.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

Nazwa         | Opis
------------ | ------------------------------------------------------
`methodType` | Synonimem . `decltype(&TDelegateInterface::Invoke)`
`Traits`     | Synonimem . `ArgTraits<methodType>`

### <a name="public-constants"></a>Stałe publiczne

Nazwa                           | Opis
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[ArgTraitsHelper::args](#args) | Pomaga [ArgTraits::args](#args) zachować liczbę parametrów `Invoke` na metodę interfejsu delegata.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ArgTraitsHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="argtraitshelperargs"></a><a name="args"></a>ArgTraitsHelper::args

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>Uwagi

Pomaga `ArgTraitsHelper::args` zachować liczbę parametrów `Invoke` na metodę interfejsu delegata.
