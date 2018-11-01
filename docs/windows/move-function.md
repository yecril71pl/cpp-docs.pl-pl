---
title: Move — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
ms.openlocfilehash: a53dbbe54cef2ac2557648e66e5d8dafc4fb4768
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591363"
---
# <a name="move-function"></a>Move — Funkcja

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template<class T>
inline typename RemoveReference<T>::Type&& Move(
   _Inout_ T&& arg
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ argumentu.

*ARG*<br/>
Argument do przenoszenia.

## <a name="return-value"></a>Wartość zwracana

Parametr *arg* po cech odwołanie lub odwołanie rvalue, jeśli zostały usunięte.

## <a name="remarks"></a>Uwagi

Przenosi określonego argumentu z jednej lokalizacji.

Aby uzyskać więcej informacji, zobacz **przenoszenie semantyki** części [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** internal.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)