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
ms.openlocfilehash: fbba6d96106cc95910ccd9d0029cb3e9c254d7d3
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335166"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Interfejs delegata.

## <a name="remarks"></a>Uwagi

Pomaga zdefiniować typowe cechy argumenty delegata.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa         | Opis
------------ | ------------------------------------------------------
`methodType` | Synonim dla `decltype(&TDelegateInterface::Invoke)`.
`Traits`     | Synonim dla `ArgTraits<methodType>`.

### <a name="public-constants"></a>Publiczne stałe

Nazwa                           | Opis
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[ArgTraitsHelper::args](#args) | Pomaga [ArgTraits::args](#args) liczbę parametrów bądź na bieżąco z `Invoke` metodę interfejsu delegata.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ArgTraitsHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="args"></a>ArgTraitsHelper::args

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>Uwagi

Pomaga `ArgTraitsHelper::args` liczbę parametrów bądź na bieżąco z `Invoke` metodę interfejsu delegata.
