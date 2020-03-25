---
title: CancelTransitionPolicy — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
helpviewer_keywords:
- CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
ms.openlocfilehash: e820b3fffb4a00e95a1210a5c0beb3229c6d1657
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214126"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy — Wyliczenie

Wskazuje, w jaki sposób operacja asynchroniczna przechodzi do stanu końcowego zakończone lub błąd powinien zachowywać się w odniesieniu do stanu anulowanego przez klienta.

## <a name="syntax"></a>Składnia

```cpp
enum CancelTransitionPolicy;
```

## <a name="members"></a>Members

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`RemainCanceled`|Jeśli operacja asynchroniczna jest obecnie w stanie anulowania żądanym przez klienta, oznacza to, że pozostanie w stanie anulowanym w przeciwieństwie do przejścia do stanu zakończenia lub błędu terminalu.|
|`TransitionFromCanceled`|Jeśli operacja asynchroniczna jest obecnie w stanie anulowania żądanym przez klienta, oznacza to, że stan powinien przejść z tego stanu, aby stan został anulowany lub błąd został określony przez wywołanie, które wykorzystuje tę flagę.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** Async. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)
