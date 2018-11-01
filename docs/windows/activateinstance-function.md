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
ms.openlocfilehash: 65648d62657bf989d4a08660e0fd7724511350c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666300"
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

*wystąpienia*<br/>
Po zakończeniu tej operacji, odwołanie do wystąpienia *T*.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie błąd HRESULT, która wskazuje przyczynę błędu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Windows::Foundation

## <a name="see-also"></a>Zobacz też

[Windows::Foundation, przestrzeń nazw](../windows/windows-foundation-namespace.md)