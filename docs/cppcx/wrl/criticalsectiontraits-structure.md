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
ms.openlocfilehash: 05c93bf6a2765bd11489075067c627ab3c3ab691
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372578"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits — Struktura

Specjalizuje się `CriticalSection` obiekt do obsługi nieprawidłowej sekcji krytycznej lub funkcji do wydania sekcji krytycznej.

## <a name="syntax"></a>Składnia

```
struct CriticalSectionTraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

Nazwa   | Opis
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | A, `typedef` który definiuje wskaźnik do sekcji krytycznej. `Type`jest zdefiniowany jako `typedef CRITICAL_SECTION* Type;`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                       | Opis
---------------------------------------------------------- | -----------------
[CriticalSectionTraits::GetInvalidValue](#getinvalidvalue) | Specjalizuje się `CriticalSection` w szablonie, dzięki czemu szablon jest zawsze nieprawidłowy.
[CriticalSectionTraits::Odblokuj](#unlock)                   | Specjalizuje się `CriticalSection` szablon, dzięki czemu obsługuje zwalnianie własności określonego obiektu sekcji krytycznej.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CriticalSectionTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki::HandleTraits

## <a name="criticalsectiontraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>CriticalSectionTraits::GetInvalidValue

Specjalizuje się `CriticalSection` w szablonie, dzięki czemu szablon jest zawsze nieprawidłowy.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wskaźnik do nieprawidłowej sekcji krytycznej.

### <a name="remarks"></a>Uwagi

Modyfikator `Type` jest `typedef CRITICAL_SECTION* Type;`zdefiniowany jako .

## <a name="criticalsectiontraitsunlock"></a><a name="unlock"></a>CriticalSectionTraits::Odblokuj

Specjalizuje się `CriticalSection` szablon, dzięki czemu obsługuje zwalnianie własności określonego obiektu sekcji krytycznej.

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>Parametry

*Cs*<br/>
Wskaźnik do obiektu sekcji krytycznej.

### <a name="remarks"></a>Uwagi

Modyfikator `Type` jest `typedef CRITICAL_SECTION* Type;`zdefiniowany jako .

Aby uzyskać więcej informacji, zobacz **LeaveCriticalSection, funkcja** w sekcji **Funkcje synchronizacji** dokumentacji interfejsu API systemu Windows.
