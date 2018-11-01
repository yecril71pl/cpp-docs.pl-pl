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
ms.openlocfilehash: 99ca0c475d7fe700c2350ae05a87b8e64b10d775
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509970"
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

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)