---
title: ActivateInstance — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
ms.openlocfilehash: 43aa34153f0e71dd665090243ff2288bff704404
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029083"
---
# <a name="activateinstance-function"></a>ActivateInstance — Funkcja

Rejestruje i pobiera wystąpienia danego typu zdefiniowane w identyfikatorze określonej klasy.

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
inline HRESULT ActivateInstance(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, aby aktywować.

*activatableClassId*<br/>
Nazwa Identyfikatora klasy, który definiuje parametru *T*.

*instance*<br/>
Po zakończeniu tej operacji, odwołanie do wystąpienia *T*.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie błąd HRESULT, która wskazuje przyczynę błędu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Windows::Foundation

## <a name="see-also"></a>Zobacz także

[Windows::Foundation, przestrzeń nazw](windows-foundation-namespace.md)