---
title: CancelTransitionPolicy, wyliczenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
dev_langs:
- C++
helpviewer_keywords:
- CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: abc49a62e1cc9fb4abdc56b329b8fa057edebde7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583520"
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