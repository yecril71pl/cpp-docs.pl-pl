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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398761"
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

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)