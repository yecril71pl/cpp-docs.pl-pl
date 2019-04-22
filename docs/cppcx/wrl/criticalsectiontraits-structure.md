---
title: CriticalSectionTraits — Struktura
ms.date: 09/26/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock method
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
ms.openlocfilehash: ce904ecbd9a5855c63fd43f07f88c215cef544ae
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58787366"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits — Struktura

Specjalizuje się `CriticalSection` obiekt na potrzeby obsługi nieprawidłową sekcję krytyczną lub funkcję, aby zwolnić sekcję krytyczną.

## <a name="syntax"></a>Składnia

```
struct CriticalSectionTraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa   | Opis
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | A `typedef` definiujący wskaźnikiem na sekcję krytyczną. `Type` jest zdefiniowany jako `typedef CRITICAL_SECTION* Type;`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                       | Opis
---------------------------------------------------------- | -----------------
[CriticalSectionTraits::GetInvalidValue](#getinvalidvalue) | Specjalizuje się `CriticalSection` szablonu, aby szablon zawsze jest nieprawidłowy.
[CriticalSectionTraits::Unlock](#unlock)                   | Specjalizuje się `CriticalSection` szablonu, tak że obsługuje uwalniający własności obiektu określona sekcja krytycznego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CriticalSectionTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>CriticalSectionTraits::GetInvalidValue

Specjalizuje się `CriticalSection` szablonu, aby szablon zawsze jest nieprawidłowy.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wskaźnik do Nieprawidłowa sekcja krytycznego.

### <a name="remarks"></a>Uwagi

`Type` Modyfikator jest zdefiniowany jako `typedef CRITICAL_SECTION* Type;`.

## <a name="unlock"></a>CriticalSectionTraits::Unlock

Specjalizuje się `CriticalSection` szablonu, tak że obsługuje uwalniający własności obiektu określona sekcja krytycznego.

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>Parametry

*CS*<br/>
Wskaźnik do obiektu sekcję krytyczną.

### <a name="remarks"></a>Uwagi

`Type` Modyfikator jest zdefiniowany jako `typedef CRITICAL_SECTION* Type;`.

Aby uzyskać więcej informacji, zobacz **funkcja LeaveCriticalSection** w **funkcji synchronizacji** części dokumentacji interfejsu API Windows.
