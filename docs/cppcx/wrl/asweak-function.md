---
title: AsWeak — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
ms.openlocfilehash: 45df6332fccb2a22284eb6478c7554d87318ca78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398852"
---
# <a name="asweak-function"></a>AsWeak — Funkcja

Pobiera słabe odwołanie do określonego wystąpienia.

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
HRESULT AsWeak(
   _In_ T* p,
   _Out_ WeakRef* pWeak
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Wskaźnik do typu parametru *p*.

*p*<br/>
Wystąpienie typu.

*pWeak*<br/>
Po zakończeniu tej operacji, wskaźnik do słabe odwołanie do parametru *p*.

## <a name="return-value"></a>Wartość zwracana

S_OK, jeśli operacja się powiedzie; w przeciwnym razie błąd HRESULT, która wskazuje przyczynę błędu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)