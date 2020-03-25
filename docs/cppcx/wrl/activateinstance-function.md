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
ms.openlocfilehash: d1109e769352d412df8348822e05b66063159ee8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214230"
---
# <a name="activateinstance-function"></a>ActivateInstance — Funkcja

Rejestruje i Pobiera wystąpienie określonego typu zdefiniowane w określonym IDENTYFIKATORze klasy.

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
inline HRESULT ActivateInstance(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance
);
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ do uaktywnienia.

*Wpisy*<br/>
Nazwa identyfikatora klasy, który definiuje parametr *T*.

*np*<br/>
Po zakończeniu tej operacji odwołanie do wystąpienia *T*.

## <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie błąd HRESULT, który wskazuje przyczynę błędu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** Client. h

**Przestrzeń nazw:** Windows:: Foundation

## <a name="see-also"></a>Zobacz też

[Windows::Foundation, przestrzeń nazw](windows-foundation-namespace.md)
