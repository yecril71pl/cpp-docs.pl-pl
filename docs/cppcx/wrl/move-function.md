---
title: Move — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
ms.openlocfilehash: 1a03216197462090f38d3bc2065fe227f0667919
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787342"
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

Aby uzyskać więcej informacji, zobacz **przenoszenie semantyki** części [Rvalue Reference Declarator: & &](../../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)