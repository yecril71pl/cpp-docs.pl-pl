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
ms.openlocfilehash: cb07f28794d466dde08719057a21ebf62f989e85
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038057"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy — Wyliczenie

Wskazuje, jak operacja asynchroniczna użytkownika próba przejście w stan końcowy ukończone lub błąd powinien działać względem klient zażądał stanem anulowane.

## <a name="syntax"></a>Składnia

```cpp
enum CancelTransitionPolicy;
```

## <a name="members"></a>Elementy członkowskie

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`RemainCanceled`|Jeśli operacja asynchroniczna jest aktualnie klient zażądał stanem anulowane, oznacza to, że pozostaną ze stanem anulowane, w przeciwieństwie do terminal ukończone lub stan błędu.|
|`TransitionFromCanceled`|Jeśli operacja asynchroniczna jest obecnie klient zażądał stanem anulowane, wskazuje to, że stan powinien przejść przy jego użyciu stanem anulowane na stan końcowy ukończone lub błąd zgodnie z ustaleniami wywołanie, które korzysta z tej flagi.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL — Przestrzeń nazw](microsoft-wrl-namespace.md)