---
title: Swap — funkcja (WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Swap
ms.assetid: ed134a08-ceb7-4279-aa02-a183c3a426ea
ms.openlocfilehash: 97d24f1f4453e948c621651e029254db1b0de712
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027567"
---
# <a name="swap-function-wrl"></a>Swap — funkcja (WRL)

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
WRL_NOTHROW inline void Swap(
   _Inout_ T& left,
   _Inout_ T& right
);
```

### <a name="parameters"></a>Parametry

*left*<br/>
Pierwszy argument.

*right*<br/>
Drugi argument.

## <a name="return-value"></a>Wartość zwracana

## <a name="remarks"></a>Uwagi

Zamienia wartości dwóch określonych argumentów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)